---
title: "Gentoo Minimal Install Problem"
date: 2010-06-06
forum: General Help
---

### Post by warrior_juggalo on 2010-06-06
I've installed minimal install of gentoo and when i reboot i choose Gentoo from Grub, it start's loading than this comes up, if i enter my password i get to a "(none) ~ #"
If that all the minimal install is, Do i start working on getting gnome up on it or do i have to fix the error bellow before moving on?


*Checking root filesystem...
fsck.ext3:Bad magic number in super-block while trying to open /dev/sda2
/dev/sda2:
The superblock could not be read or does not describe a correct ex2
filesystem. If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
e2fsck -b 8193 <device>

*Filesystem couldn't be fixed
give root password for maintenance
(or type Control-D to continue): _

---

### Post by wooblah on 2010-06-06
if it isnt broken dont fix it thats what i say.
didnt you set your hostname on install ?
your description is completely cryptic i dont see how anyone can figure out what the hell you are on about, but if you get a prompt im assuming you dont have the system on /dev/sda2. 
or perhaps your install or disk is borked and you get this before a proper boot, thats the unclear bit to me.

emerge gnome 

see you in a couple of days.  ahhhhhh gentoo :)

---

### Post by GlazedDonut on 2010-06-06
It is trying to check /dev/sda2, which is apparently your root filesystem, and fails:
> **warrior_juggalo said:**
> 
*Checking root filesystem...
fsck.ext3:Bad magic number in super-block while trying to open /dev/sda2
/dev/sda2:
The superblock could not be read or does not describe a correct ex2
filesystem. If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
e2fsck -b 8193 <device>

So it dumps you in single-user mode to fix the problem
> 
*Filesystem couldn't be fixed
give root password for maintenance
(or type Control-D to continue): _

This is not the normal operating state of the system, you need to fix whatever it is in single user mode and then reboot. Try manually checking the root file system:
fsck /dev/sda2

sometimes thats enought to fix errors like this.

---

### Post by wooblah on 2010-06-06
oh y

---

### Post by GlazedDonut on 2010-06-06
> **wooblah said:**
> oh y

Because he also posted this:

> **warrior_juggalo said:**
> 
*Checking root filesystem...
fsck.ext3:Bad magic number in super-block while trying to open /dev/sda2
/dev/sda2:
The superblock could not be read or does not describe a correct ex2
filesystem. If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
e2fsck -b 8193 <device>

*Filesystem couldn't be fixed
give root password for maintenance
(or type Control-D to continue): _

---

### Post by wooblah on 2010-06-06
yeah but he wasnt clear on whether it threw an error on startup or whether he just pulled that out of somewhere else, dmesg n such.  although, y im stupid :)

---

