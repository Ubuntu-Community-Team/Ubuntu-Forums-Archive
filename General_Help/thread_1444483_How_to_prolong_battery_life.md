---
title: "How to prolong battery life?"
date: 2010-04-01
forum: General Help
---

### Post by Phentis on 2010-04-01
Good Day!

I am new to Ubuntu. I have a Samsung R510 laptop, with a short-life battery (holds up to 1.5 hours)

Is there any way to make my laptop work longer by using some tweaks? Maybe it is possible to change the CPU according to the load?

Please, note that I am new to Ubuntu and to linux in general.

Thanks in advance!

---

### Post by Martje_001 on 2010-04-01
Try Intel's program 'powertop'. You can install it using Synaptic and run it in the terminal :). The program provides information about how to prolong your laptop's battery life.

---

### Post by Phentis on 2010-04-05
Thanks, I used it, but it gives general advices, like disabling some devices, wifi, bluetooth, etc.

BTW, what does this mean?:
[IMG]http://s50.radikal.ru/i128/1004/70/ebf4bbf00976.jpg[/IMG]

I have read about powernowd, but I can't understand, how to use it. I will be very glad if someone helps me :)

Thanks in advance!

---

### Post by Martje_001 on 2010-04-05
Those are states the processor could be put into:
> The CPU power states C0-C3 are defined as follows:

    * C0 is the operating state.
    * C1 (often known as Halt) is a state where the processor is not executing instructions, but can return to an executing state essentially instantaneously. Some processors, such as the Pentium 4, also support an Enhanced C1 state (C1E or Enhanced Halt State) for lower power consumption,[7] all processors must support this power state.
    * C2 (often known as Stop-Clock) is a state where the processor maintains all software-visible state, but may take longer to wake up, this processor state is optionally supported by the system.
    * C3 (often known as Sleep) is a state where the processor does not need to keep its cache coherent, but maintains other state. Some processors have variations on the C3 state (Deep Sleep, Deeper Sleep, etc.) that differ in how long it takes to wake the processor. This processor state is optionally supported by the system.
[SIZE="1"]Source: [http://en.wikipedia.org/wiki/Advanced_Configuration_and_Power_Interface](http://en.wikipedia.org/wiki/Advanced_Configuration_and_Power_Interface)[/SIZE]

Powernowd is a kernel-module. Only advanced users (no offence!) are meant to be tinkering with it ;). You could still try though:

1. [http://www.thinkwiki.org/wiki/How_to_make_use_of_Dynamic_Frequency_Scaling](http://www.thinkwiki.org/wiki/How_to_make_use_of_Dynamic_Frequency_Scaling)
2. [http://www.thinkwiki.org/wiki/How_to_configure_powernowd](http://www.thinkwiki.org/wiki/How_to_configure_powernowd)

---

