---
title: "Ubuntu 9.10 boots unreliably and slowly, but gets past GRUB"
date: 2010-03-03
forum: General Help
---

### Post by WarriorIng64 on 2010-03-03
I have had a desktop computer rebuilt recently by a computer shop, with the hard drive left blank so I could install Ubuntu 9.10 64-bit on it. This is not a dual-boot machine; Ubuntu is the only OS on there.

The problem is that the computer can be very difficult to boot. I'm not saying impossible because sometimes it will work for me, but only after a very long wait, and most of the time it simply gets stuck and never boots. I have had Ubuntu successfully installed and used on both my previous desktop and my laptop in a dual-boot configuration, and I have never encountered this type of problem before.

The problem does not seem to be GRUB, at least not from what I can tell. I am using the latest version of it on both my laptop and current desktop, and it seems to come up just fine. On the desktop (where I'm having the problem), after choosing to boot Ubuntu, the system will come to the blank screen with a flashing cursor, hang there for a couple minutes, then proceed to either the screen with the white Ubuntu logo in the center (now it will load) or it stays in a completely blank black screen until I cut the power (this is most of the time).

At any rate, this is not going to be sufficient for my personal use, and I'm hoping someone might have an idea of how I can make the computer boot reliably and quickly. My only problem is with booting; on the times I can get it to boot successfully, the system runs very quickly and smoothly, with no further issues.

Here is some hardware being used if it will help in diagnosing the problem. Everything listed below is new except where otherwise noted:

[LIST]
[*]Two IDE DVD-RW drives (the main one's old, the second one's not)
[*]A 320GB SATA hard drive
[*]An AMD X2 250 processor
[*]2GB RAM
[*]A floppy drive (pretty old; still works as far as I know)
[*]A wireless internet card that still works (a couple years old)
[*]Gigabyte GA-M61PME-SP2 motherboard
[*]300W ATX power supply
[/LIST]
Some other things that may be helpful: it uses a PS/2 mouse, a USB keyboard, a VGA display, and the onboard NVIDIA graphics (no separate graphics card). I've only managed to get it to boot so far when the Ethernet cable I use to connect online is left unplugged. I have tried (unsuccessfully) to boot into Recovery Mode, and before it froze the system output a number of hardware errors about links being slow or stuff like that. If anyone has any ideas, I'd appreciate it.

---

### Post by mgranet on 2010-03-03
Can you post the output of ```
cat /var/log/kern.log
```

---

### Post by WarriorIng64 on 2010-03-03
I ran the requested command in my terminal, and it seemed to take a really long time just outputting a bunch of what appeared to be error messages over and over. I eventually used Control + C to kill it after a minute and looked up the log file in my file browser, and it was 14.3 MB big. When I opened it to take a look, just the beginning looked different, but most of it was the same error stuff.

Did you want me to post a particular section of text from this file, or should I find a way to attach it? I seriously doubt you want me to copy/paste that whole thing.

As an example of what I'm talking about:
```
Mar  2 20:52:32 Xyz kernel: [  970.058396] phy0 -> rt2x00pci_regbusy_read: Error - Indirect register access failed: offset=0x0000308c, value=0xffffffff
Mar  2 20:52:32 Xyz kernel: [  970.059000] phy0 -> rt2x00pci_regbusy_read: Error - Indirect register access failed: offset=0x0000308c, value=0xffffffff
Mar  2 20:52:32 Xyz kernel: [  970.059604] phy0 -> rt2x00pci_regbusy_read: Error - Indirect register access failed: offset=0x0000308c, value=0xffffffff
Mar  2 20:52:32 Xyz kernel: [  970.060208] phy0 -> rt2x00pci_regbusy_read: Error - Indirect register access failed: offset=0x0000308c, value=0xffffffff
Mar  2 20:52:32 Xyz kernel: [  970.060812] phy0 -> rt2x00pci_regbusy_read: Error - Indirect register access failed: offset=0x0000308c, value=0xffffffff
Mar  2 20:52:32 Xyz kernel: [  970.060915] phy0 -> rt61pci_wait_bbp_ready: Error - BBP register access failed, aborting.
Mar  2 20:52:32 Xyz kernel: [  970.060919] phy0 -> rt61pci_set_device_state: Error - Device failed to enter state 4 (-5).
```This seems like the typical section that repeats over and over again.

---

### Post by oldfred on 2010-03-03
Are you using the wireless?

This solved says the wireless was misconfigured and was causing the problem.
[http://wicd.net/punbb/viewtopic.php?id=594](http://wicd.net/punbb/viewtopic.php?id=594)
The problem is resolved !!  In the network settings, there was WPA instead of WEP.

---

### Post by WarriorIng64 on 2010-03-03
I think the problem may be resolved now, but it wasn't because of the wireless. It was actually the physical configuration of the DVD-RW drives.

After a bit of fooling around with BIOS values, I found settings that would let me boot into Ubuntu every time so long as a disc of some sort was in one of the optical drives at the time of boot. It didn't matter what it was--it could even be a blank CD--but the system would only boot if the disc was there and would get stuck after GRUB if it wasn't. (I also found through further experimentation that whether the computer was connected by Ethernet or not had no effect on whether the OS would boot.)

I took the desktop back to the computer shop where it was built, the owner took a quick look inside and yelled at one of his employees for setting both optical drives as master, instead of one of them being slave. He fixed it free of charge for me, and now I can boot the system every time. :D

I am typing this reply on the machine that was previously affected, and am now quite pleased with it. Who would have thought the cause of the problem would be something so simple?

Thanks anyways to everyone who helped me up to this point.

---

