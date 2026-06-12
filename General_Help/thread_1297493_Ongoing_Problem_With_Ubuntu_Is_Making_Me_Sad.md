---
title: "Ongoing Problem With Ubuntu Is Making Me Sad"
date: 2009-10-21
forum: General Help
---

### Post by xenocution on 2009-10-21
I love Ubuntu and have been a admirer since Gutsy Gibbon. But in every flavor and version I've installed I keep having the same problem. After a seemingly random amount of time apps just quit working, and if I close an app or start up a new one it will begin to run...then nothing. It's almost as if the app is not released from memory. 

Also, when I try to reboot it hangs on shut down.

I'm dual-booting with Win XP and don't have any hardware trouble (or the same problem) in that OS.

My machine is a AMD Athlon 1097.888 MHz Processor, 623 MiB RAM, and 2 GB Swap (yeah probably a bit bigger swap than I need).

I'm currently running Kubuntu 5.0, 2.6.28-15-generic kernel. (I've also tried Ubuntu and Xubuntu and had the same problem.)

If anyone has the time and patience to help me with this problem I'd really appreciate it! 

Please let me know what other information I need to provide.

**TIA.**

---

### Post by Johnny B on 2009-10-21
since it happens with all the distros you tried, the first thing i would do is check the hardware
try memtest on the live cd

---

### Post by xenocution on 2009-10-22
> **Johnny B said:**
> try memtest on the live cd

Thanks for the reply. I ran memtest and had zero errors.

---

### Post by KlinerDraken on 2009-10-22
The next thing you can try is run one of the programs that locks up from the command line. See if you get an error message that might help find the root cause of the issue.

---

### Post by pgar23 on 2009-10-22
> **KlinerDraken said:**
> The next thing you can try is run one of the programs that locks up from the command line. See if you get an error message that might help find the root cause of the issue.

I second this idea. 

That's one thing that I like about Ubuntu. You can traceback the root of an error rather than receiving some craptacular error message from winblows that doesn;t supply any solutions.

---

### Post by tgalati4 on 2009-10-22
Check /var/log for errors.  Post any of interest.

---

### Post by xenocution on 2009-11-07
SOLVED! (I hope) :D

It's been two days and no crash so far. I think the problem was caused by ndiswrapper crashing the kernel.

Following this suspicion I bought a **Sabrent 2.4ghz 802.11G** wireless pci card. It comes with Linux drivers and is already supported in Ubuntu 9.10.

And so far, so good.

Hopefully this info will help others with a similar problem, or folks who are looking for a wireless pci adapter card which supports Linux.

---

