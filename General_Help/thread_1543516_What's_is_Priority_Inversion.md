---
title: "What's is Priority Inversion?"
date: 2010-08-01
forum: General Help
---

### Post by meoconvn38 on 2010-08-01
I have study about the Real Time OS , and try to patch the RTAI to ubuntu , what i have still concern is that the difference between RTOS and normal OS, and the priority inversion is one of problems :(

---

### Post by worksofcraft on 2010-08-02
In general purpose OS like Windows and Linux, the concept of priority is related to what percentage of processing time is devoted to each process.

For a real-time operating system, priority is related to latency. i.e how long it will take to service an event.

The scheduler in general purpose OS is mostly based on time slices. The operating system has little understanding of the concept of latency.

For instance you might notice irregularity in rhythm when synthesizing music under Windows or Linux, simply because the OS doesn't realize that for you the audio output is much more URGENT than updating the display even though it might need nowhere near as much processing time.

Priority inversion occurs when a low priority task is using a resource e.g. disk drive, and high priority task has to queue and wait for it's turn even though it is higher priority. Where timing is critical you can see this could have devastating consequences.

The scheduler in RTOS is based on interrupts. Unlike in ordinary OS the interrupt does not return to the interrupted process, but to scheduler who then chooses whatever active task is of highest priority. The interrupted process will only be resumed when there is NOTHING of higher priority that needs to be done.

Example:

On a desktop computer you might write a program that sits in a loop waiting for a key press. If you did that on a RTOS then absolutely NOTHING below that priority would get done even though all it is doing is looping aimlessly. OTOH if you drop the priority while it is looping then, when the key is pressed, it might take ages to notice and respond (unacceptable latency).

On RTOS that process would have to be programmed to suspend itself and rely on an interrupt to tell the scheduler when the key is pressed. That way it can respond immediately with it's original high priority.

Does this explanation help?

---

### Post by meoconvn38 on 2010-08-02
:D very good I understand now :popcorn:

---

