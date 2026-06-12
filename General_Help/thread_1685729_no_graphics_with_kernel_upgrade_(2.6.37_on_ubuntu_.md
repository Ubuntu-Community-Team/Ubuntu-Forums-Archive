---
title: "no graphics with kernel upgrade (2.6.37 on ubuntu 10.10)"
date: 2011-02-11
forum: General Help
---

### Post by MrPolite on 2011-02-11
Hi all, 
I am a noob :)
I upgraded my kernel from 2.6.35-22-generic to 2.6.37...

when I reboot to the new kernel, i only get a tty prompt to log in, with no GUI. How can I find out what's wrong with the graphics?

---

### Post by archvortex on 2011-02-11
It's probably a compatibility issue with your graphics drivers and the kernel. You didn't say what graphics card you're using. Why do you want to use the 2.6.37 kernel? I don't see it in the synaptic (I'm running Maverick too). You say you're a noob so I would suggest upgrading to the 2.6.35.24 or 2.6.35.25 in your synaptic first to see if your graphics are compatible. Then read the kernel forums about your graphics card and the 2.6.37 kernel. This site, [Linux Kernel Newbies]("http://kernelnewbies.org/"), and its web forum will also be helpful for you. Good luck!!

Stan

---

### Post by mastablasta on 2011-02-11
how did you install the system? via Wubi?

---

### Post by MrPolite on 2011-02-11
Thanks for the replies!
yes I installed ubuntu via wubi then upgraded the kernel... is that a problem?

I don't actually know what graphics card it's using :( The reason i installed 2.6.37 is because I wanted to add the CONFIG_ACPI_EC_DEBUGFS option, which didn't exist in my kernel.

---

