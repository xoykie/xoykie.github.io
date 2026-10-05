# CPU can do it. But should it?

Given a task that must be repeated a lot, more or less uniformly, a specialised hardware can be designed to do that task without the need of CPU. This saves CPU cycles, which can be used elsewhere.

For example, say we have a repetitive task:
  Check network packet for errors using checksums and error-detection codes.
  If an error is detected, request that packet to be resent.

Technically, this tasks can be done by a CPU. But what if we create a dedicated hardware for this uniformly repetitive task?
And that's where NIC enters the scene. NIC can do this task(and many more tasks listed at\[[1]\]) independent of the CPU.

Whatever NIC does can be done by the CPU as well. In fact you can simulate/emulate NIC on a CPU. Not just NIC, many other tasks for which dedicated hardwares exist can be done by the CPU.
But why waste CPU cycles on frequent repetitive tasks? In our case here, using NIC will save CPU cycles.
Secondly, a dedicated hardware unit(here, NIC) will be more efficient than a generalised-hardware i.e. CPU.


Let's take another example. Say, we have a repetitive task:
  When a key is pressed from the keyboard, receive it, and store it in memory.

A CPU can do this. But since keypresses happen too frequently and the task of receiving and storing is uniformly repetitive, it'd be better to design a dedicated hardware unit to handle it.
A dedicated hardware unit that handles this is called Direct Memory Access(DMA). DMA takes this responsibility so our CPU can be free for other tasks.
And the use of DMA doesn't need to be limited to keypresses from a keyboard. It can also be used to store data received from a microphone, or a camera.
You can read more about what other uniformly repetitive tasks DMA does here\[[2]\]

A cutting edge example before we end this article. One can classify scheduling processes as a repetitve task. And therefore, there have been some attempts to do this using
dedicated hardware units. While scheduling can be called a repetitive task, it's less uniform than the two examples above. The scheduling algorithms are more dynamic and nuanced than the tasks lists above.

Hence, there are challenges in creating a hardware dedicated to scheduling.

Examples of attempts made to design specialised hardware for scheduling processes(this part is not ready for publishing. needs to search more):

1. ARM Cortex-M (NVIC + SysTick):

The NVIC (Nested Vectored Interrupt Controller) provides hardware-based interrupt prioritization and fast context switching.

SysTick timer gives a hardware time base for the RTOS tick. While not a full scheduler, it heavily accelerates RTOS scheduling.


2. Real-Time Hardware Schedulers (Dedicated IP Blocks): Some SoCs and FPGAs implement a complete hardware scheduler as a logic block.

SEOS / hardware RTOS accelerators – manage task queues, priorities, and switching entirely in hardware.

RTU (Real-Time Unit) – a well-known academic hardware scheduler design that offloads RTOS kernel functions.


3. Sitara / Specialized Processors with PRU: TI's PRU (Programmable Real-Time Unit) – a dedicated real-time core that handles time-critical tasks independently of the main CPU.

4. FPGA-Based RTOS Schedulers: Engineers implement custom hardware schedulers on FPGAs for applications needing ultra-precise timing. Fully customizable priority and scheduling logic in hardware.



Bibliography:

\[1\]: https://www.fs.com/blog/what-is-a-network-interface-card-nic-definition-function-types-525.html

\[2\]: https://www.spiceworks.com/it-hardware/direct-memory-access/

[1]: https://www.fs.com/blog/what-is-a-network-interface-card-nic-definition-function-types-525.html
[2]: https://www.spiceworks.com/it-hardware/direct-memory-access/
