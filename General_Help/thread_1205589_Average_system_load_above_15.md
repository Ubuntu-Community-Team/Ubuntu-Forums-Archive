---
title: "Average system load above 15?"
date: 2009-07-06
forum: General Help
---

### Post by Nixie Pixel on 2009-07-06
Hi, I'm having problems with a laptop running Ubuntu Studio 8.10. I noticed that sometimes when I left it idle it would freeze and I had to use the power button to restart it.

I turned on all of the panel options for system monitor, and kept system monitor open. I noticed that when I tried to install openoffice today, the "average system load" kept going up and up, to well over 15, and I couldn't do anything at all. I couldn't even get it to open a terminal window.

Since it froze in the middle of synaptic trying to install openoffice for me, when I tried to open synaptic again it told me to run sudo dpkg --configure -a. I did this, and watched my process monitor, I had no runaway processes. No process that took up a large portion of CPU time, nothing that took up a lot of memory, yet while it was trying to fix the openoffice install my "system load average" kept going up and up and up, until it got above 5, above 8...all the way to 15. The computer stopped responding to commands, even CTRL-C at the terminal to stop the dpkg process.

So my questions are: what exactly is "system load average" on the process monitor panel, what does it mean to me, and why is it so high, causing the computer to freeze, when no process appears to be taking up a high amount of CPU time or memory (all the other monitors are normal, and the process tree shows nothing abnormal)? Even CTRL-ALT-F1 and CTRL-ALT-BACKSPACE do nothing when the system load gets this high, and I am now unable to use the laptop.

Thanks!

---

### Post by Nixie Pixel on 2009-07-06
Some additional info:
I have no network mounts.
Running dmesg (before the load gets too high) gives me a bunch of info I don't understand, including the message:
Fixing recursive fault, reboot is needed!

Unfortunately I can't reboot as the system becomes unresponsive at that point.

---

### Post by regala on 2009-07-06
> **Nixie Pixel said:**
> Some additional info:
I have no network mounts.
Running dmesg (before the load gets too high) gives me a bunch of info I don't understand, including the message:
Fixing recursive fault, reboot is needed!

Unfortunately I can't reboot as the system becomes unresponsive at that point.

Do you have access to the few lines before Fixing-bla ? Seems like a bug in your latest kernel. Have you run this kernel without problem in the past ? do you have another kernel from before ? If you can post what gives dmesg | tail -n 50, it would be kind.

Thanks and be brave, I hope you have another kernel.


oh, I forgot: Load average is "real-time" calculated mean, of the number of processes, at a time, asking for a resource, especially the cpu(s) and block devices. here it seems that a filesystem or a block disk triggers an oops (a segfault in kernel space) and that this resource is not available anymore. At this point any process spawned asking for it is stuck "for ever", adding to load average.

---

