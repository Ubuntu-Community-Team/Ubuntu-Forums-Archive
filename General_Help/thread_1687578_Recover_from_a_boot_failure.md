---
title: "Recover from a boot failure?"
date: 2011-02-14
forum: General Help
---

### Post by nailujc on 2011-02-14
Had Ubuntu 10.10  running fine on a Dell box, shut down as normal earlier in the week but  now won't boot from GRUB (ends up with Busybox screen and initramfs(?)  prompt).  PC is a dual boot system which still boots OK into the XP  partition on the same hard disk.  I've tried all the other Unbuntu boot  options in the GRUB menu (older kernels and the 'recovery' /  non-recovery options) but all produce the same failure to boot into  Ubuntu.  I've searched the forums and tried various things but nothing  has worked so far.

I tried the fix of booting from an Ubuntu 10.10 live CD, creating a  mount point and mounting the relevant linux partition before using  #apt-get update and #apt-get upgrade options to repair the installation.   This seemed like a logical simple solution BUT the partition will not  mount!!  Further investigation using the Disk Utility app in the Ubuntu  drop down menu indicated an error message along the lines of 'cannot  mount Daemon inhibited' which I can't seem to find much information  about fixing.

Using Gparted it looks like all the partitions originally set up on the disk are still there.

As a linux newbie I put a lot of time into getting the system set up  (scanners, printers, webcams and software) and would be really annoyed  to have to do it all again if at all possible ...

Can anyone help me further diagnose the specific problem and how it could be fixed???

---

### Post by MiKOTRON on 2011-02-14
[LEFT]Besides mounting your HDD you need to chroot into your system in order for any repairs to be done.  Otherwise you're just making changes to your virtual environment loaded in RAM.
[/LEFT]

---

### Post by nailujc on 2011-02-21
Think I'm gonna have to give up and re-install.

Can see the partitions in GParted but can't mount them at all either through terminal commands or other means within Linux. Even tried using IFS drives in Windows XP which allows reading of Linux ext(x) partitions in Windows - it reported the partitions as not formatted).  As I can't mount them I've not even got to the point of using 'chroot'

Is there any sort of low level scan of the disk I could try to at least know if the partition has been corrupted / has bad sectors etc.

---

