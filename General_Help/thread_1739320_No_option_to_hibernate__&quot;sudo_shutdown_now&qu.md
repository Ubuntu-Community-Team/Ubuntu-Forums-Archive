---
title: "No option to hibernate / &quot;sudo shutdown now&quot; causes crash"
date: 2011-04-25
forum: General Help
---

### Post by nrabett on 2011-04-25
I assume that the two issues are related.

Gigabyte P55-USB3 mobo,
ATI Radeon HD 5800 Series graphics card,
8 GB ram

Ubuntu installed after Win7.

Dual boot Win7 and Ubuntu 10.04, shared NFTS partition for Downloads and Documents, Grub setup to load Ubuntu by default. I can use the option to hibernate in Windows (but it is disabled by default).

I would very much like to enable the "Hibernate" function on this machine, but there is no option for it in the menus.

"sudo shutdown now" in a Terminal results in a screen that resembles the login screen background, but the machine is completely irresponsive and must be silenced by long-pressing the physical power button. When I use the GUI to shut down, everything works fine.

Perhaps related: When waking the machine from the screen saver, the login window does not turn up before I press the "Esc" button. I am using a standard Gnome screen saver.

Perhaps related: The Grub boot screen is getting more and more options every time the Linux kernel is updated. sudo grub-update does not help.

Please do not lead me to the Ubuntu manual page

[https://help.ubuntu.com/9.10/hardware/C/pm-suspending.html](https://help.ubuntu.com/9.10/hardware/C/pm-suspending.html)

which has a well-known, dead link.

---

### Post by JKyleOKC on 2011-04-25
For hibernation to work in Ubuntu, you must have a swap partition established that is at least as large as your total amount of RAM since hibernation will dump all RAM to the swap partition. It's best to make it at least a bit larger for safety's sake.

The additional options on the grub menu with each kernel update are completely unrelated to the hibernation and shutdown problems. The update procedure never removes an old set of kernel files, just in case you might need to fall back on them (I've had to drop back by two revisions at least once, before I learned how to keep my video drivers up to date). To trim the list back you have a number of options. The simplest is to install and use "Grub Customizer" (search for that name to find threads detailing what it is and how to use it). If you want to reclaim some disk space, you can use the Synaptic Package Manager to locate and remove all but the most recent two.

---

### Post by nrabett on 2011-04-25
Aha, the Swap partition is only 1.2 GB. I run Ubuntu and Windows from a SSD (storage and shared NFTS partition is on another HD), and the space is limited.

---

### Post by collisionystm on 2011-04-25
Dont use shutdown now

```

shutdown -P 0

```

---

### Post by nrabett on 2011-04-30
> **collisionystm said:**
> Dont use shutdown now

```

shutdown -P 0

```

Thanks, this works.

---

