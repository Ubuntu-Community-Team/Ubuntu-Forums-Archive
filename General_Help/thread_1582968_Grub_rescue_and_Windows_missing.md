---
title: "Grub rescue and Windows missing?"
date: 2010-09-27
forum: General Help
---

### Post by Whippersnapper on 2010-09-27
I have a Dell Vostros 1500 laptop with two partitions. The C drive contains Windows XP Pro, and I installed Ubuntu 9.04 via Wubi on the D drive (partition). Both systems worked well together, with a menu available to bootup into either OS.  After booting up in Ubuntu, I attempted to upgrade to 10.04 via the update manager.  All appeared to go well, but upon rebooting of the system, I only get a “grub rescue” prompt and am unable to input any commands. Has my Windows partition been overwritten? And is there a way to downgrade back to 9.04?

---

### Post by Mark Phelps on 2010-09-27
> **Whippersnapper said:**
> ... I installed Ubuntu 9.04 via Wubi on the D drive (partition).
I believe that's the source of the problem.  I don't use Wubi but I've heard others advise against updating it.  It's really only intended for short-term usage.

> Has my Windows partition been overwritten? 
Most probably (and hopefully) not, but if you boot from a LiveCD, open a terminal, and enter "sudo fdisk -lu" (that's a lowercase L, not a one), you will see a list of partitions, and if the first partition is still there, you're probably OK.

> And is there a way to downgrade back to 9.04?
No, there is no simple way to downgrade -- another reason for NOT upgrading using Wubi.

---

### Post by Whippersnapper on 2010-09-27
Thanks for the info! How do get to terminal from the command line "grub-rescue". It seems that any entry returns "grub-rescue"

---

### Post by Whippersnapper on 2010-09-27
Sorry! I see you have to use the live CD to get to the terminal!

Thanks again.

---

### Post by bcbc on 2010-09-27
If you upgraded grub-legacy to grub2, you probably installed grub to the drive master boot record (MBR). So you need to replace that with the windows boot loader. (for xp, boot with windows repair and run "fixmbr")

Likely that's all the damage. There were problems before with installing grub2 to the windows boot sector when 10.04 was released but I believe these have been fixed now, so windows should work as normal.

I'm not sure what effect upgrading to grub2 in wubi would be - it's not likely to work, but hopefully it will still boot since many of the wubi boot files are separate in releases prior to 9.10. If you find you can't boot wubi after that, make sure you save the root.disk - you can loop mount this and recover data if need be.

---

### Post by Whippersnapper on 2010-09-28
Fixboot, and Fixmbr in the Windows recovery mode got me back into XP. Only problem: scrolling off the trackpad in any program is not smooth. It seems like I'm scrolling in waves. I'm making a new Ubuntu disk today to check my second partition.

Thanks for the help.

---

