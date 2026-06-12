---
title: "grub fails to load after vista hibernated"
date: 2010-04-26
forum: General Help
---

### Post by jacobhoi on 2010-04-26
I am new to linux, and just installed ubuntu 9.10 besides the existing windows vista partition. Everything worked smoothly. However, after I let vista go into hibernation and then started up the system again, the grub was unable to load. Instead, I got the command prompt 'GRUB rescue'. When I boot from the live CD and try to open the ubuntu partition on 'places' in the desktop environment, I get the message that it cannot be done because windows has hibernated on the other partition, and that I need to delete the hibernation file. 

The question is: What do I do to get the GRUB to load? Now I am stuck with booting from the CD, and I cannot access Vista at all. Any help is greatly appreciated!

---

### Post by carl4926 on 2010-04-26
It should normally be possible to hibernate either Vista or Ubuntu, but you must boot that OS when you start up again from hibernation.
You didn't hibernate Vista and then try to start Ubuntu did you?

Try powering off the machine and if a laptop, pull the battery. Wait a min and then try again.

If that fails try booting with SuperGrubDisk and see if it will bring Vista up.

---

### Post by P4man on 2010-04-26
Is this a wubi install? wubi is if you install ubuntu from within windows, inside the same partition. Im not sure if you can dual boot wubi when windows is hibernated, since ubuntu wont mount a hibernated windows filesystem to prevent corrupting it. Im not sure though as I dont use wubi and keep recommending against using it for many reasons.

---

### Post by jacobhoi on 2010-04-26
> **carl4926 said:**
> It should normally be possible to hibernate either Vista or Ubuntu, but you must boot that OS when you start up again from hibernation.
You didn't hibernate Vista and then try to start Ubuntu did you?

Try powering off the machine and if a laptop, pull the battery. Wait a min and then try again.

If that fails try booting with SuperGrubDisk and see if it will bring Vista up.

When Ubuntu was installed, the GRUB was automatically set to be the main loader. Normally, the GRUB will give me the option of starting up either Vista or Ubuntu. The problem now is that the GRUB itself won't start, and I cannot boot into Vista, since it is started up by GRUB. So even if I try pressing F12 directly after the BIOS has loaded, there is no option in the boot menu to load Vista. It seems as if I am stuck outside any OS when booting from the hard drive as long as I am not able to delete Vista's hibernation file.

---

### Post by carl4926 on 2010-04-26
You should be able to access: hiberfil.sys

(I think that's correct file)

Using Parted Magic

---

### Post by jacobhoi on 2010-04-26
Great, I will try that. Many thanks for your help!

---

