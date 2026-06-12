---
title: "Problems booting into Ubuntu?"
date: 2009-11-27
forum: General Help
---

### Post by lsk3993 on 2009-11-27
Help! I have Ubuntu dual booted with XP using Wubi and although I've been using it without problems for some time now when I tried booting into Ubuntu today it wouldn't work.
Instead of booting up like normal it goes to a black screen with white text saying "GNU GRUB version 1.97~beta4"
It also has some text underneath which makes no sense to me: "[ Minimal BASH-Like line editing is supported. For the first word, TAB lists possible command completions. Anywhere else TAB lists the possible completions of a device/filename. ]"
It then says sh:grub>

Presumeably I need to type in some command or something but I have no idea what to do or why this is showing up although it doesn't normally

---

### Post by amaz1ng on 2009-11-27
I'm having the same problem. I think using the proprietary graphics drivers did it for me, I'm not sure how to fix it. I might reinstall soon. :p

---

### Post by BASH-full on 2009-11-27
Same happened to me.  When Karmic did its latest update it updated GRUB 1.96 to 1.97 beta and created a GRUB boot flaw that happens with Karmic/WUBI.  Here's how to get in.

sh:grub>[B]set root=(loop0)
[/B]sh:grub>[B]linux /boot/vmlinux-2.6.31-14-generic root=/dev/sda1 loop=/ubuntu/disks/root.disk ro
[/B]sh:grub>[B]initrd /boot/initrd.img-2.6.31-14-generic
[/B]sh:grub>**boot**

It's a lot of typing, I know but it'll get you back into your OS.  This is a huge bug in Linux/GRUB. Until Ubuntu has a bug fix you'll have to enter this 140+ character incantation every time you want to boot Linux.

---

### Post by ncmncm on 2009-11-27
[https://bugs.launchpad.net/ubuntu/+bug/477169](https://bugs.launchpad.net/ubuntu/+bug/477169)

Check launchpad for Wubi and grub2 install issues

---

### Post by lsk3993 on 2009-11-27
> **BASH-full said:**
> Same happened to me.  When Karmic did its latest update it updated GRUB 1.96 to 1.97 beta and created a GRUB boot flaw that happens with Karmic/WUBI.  Here's how to get in.

sh:grub>[B]set root=(loop0)
[/B]sh:grub>[B]linux /boot/vmlinux-2.6.31-14-generic root=/dev/sda1 loop=/ubuntu/disks/root.disk ro
[/B]sh:grub>[B]initrd /boot/initrd.img-2.6.31-14-generic
[/B]sh:grub>**boot**

It's a lot of typing, I know but it'll get you back into your OS.  This is a huge bug in Linux/GRUB. Until Ubuntu has a bug fix you'll have to enter this 140+ character incantation every time you want to boot Linux.
Any idea when this will be fixed? If it's not too long I think I can wait until it's fixed, then use that 'incantation' once and install the fix.
I wrote it down anyway and thanks for shedding some light on this :D

I hate using XP, is there any quick fix by any chance?

---

### Post by ts8592 on 2009-11-27
> **amaz1ng said:**
> I'm having the same problem. I think using the proprietary graphics drivers did it for me, I'm not sure how to fix it. I might reinstall soon. :p
Same problem here, except it is happening the second time after reinstalling with Wubi.

---

### Post by ts8592 on 2009-11-27
> **BASH-full said:**
> Same happened to me.  When Karmic did its latest update it updated GRUB 1.96 to 1.97 beta and created a GRUB boot flaw that happens with Karmic/WUBI.  Here's how to get in.

sh:grub>[B]set root=(loop0)
[/B]sh:grub>[B]linux /boot/vmlinux-2.6.31-14-generic root=/dev/sda1 loop=/ubuntu/disks/root.disk ro
[/B]sh:grub>[B]initrd /boot/initrd.img-2.6.31-14-generic
[/B]sh:grub>**boot**

It's a lot of typing, I know but it'll get you back into your OS.  This is a huge bug in Linux/GRUB. Until Ubuntu has a bug fix you'll have to enter this 140+ character incantation every time you want to boot Linux.
I tried the procedure, but after typing in the second line command it indicates the file could not be found.

---

### Post by Sin@Sin-Sacrifice on 2009-11-27
It said file not found because your install isn't on /dev/sda1. You have to change that part to where your install is (ie. /dev/hda1, /dev/sda2, /dev/sdb1... etc).

---

### Post by ts8592 on 2009-11-28
> **Sin@Sin-Sacrifice said:**
> It said file not found because your install isn't on /dev/sda1. You have to change that part to where your install is (ie. /dev/hda1, /dev/sda2, /dev/sdb1... etc).
Thanks, but how do I know what the name of the install location is. My installation is on C:/ubuntu.

---

### Post by lsk3993 on 2009-11-28
I think I'll just do a proper install as opposed to using Wubi, that should get rid of the problem right?

---

### Post by kooz_jr on 2009-11-28
> **BASH-full said:**
> Same happened to me.  When Karmic did its latest update it updated GRUB 1.96 to 1.97 beta and created a GRUB boot flaw that happens with Karmic/WUBI.  Here's how to get in.

sh:grub>[B]set root=(loop0)
[/B]sh:grub>[B]linux /boot/vmlinux-2.6.31-14-generic root=/dev/sda1 loop=/ubuntu/disks/root.disk ro
[/B]sh:grub>[B]initrd /boot/initrd.img-2.6.31-14-generic
[/B]sh:grub>**boot**

It's a lot of typing, I know but it'll get you back into your OS.  This is a huge bug in Linux/GRUB. Until Ubuntu has a bug fix you'll have to enter this 140+ character incantation every time you want to boot Linux.

Hi everyone,

I have had the exact same problem, and the commands above DO solve the problem; HOWEVER, there appears to be a typo...

In the second command, it should read:
sh:grub>linux /boot/vmlinu**z**-2.6.31-14-generic root=/dev/sda1 loop=/ubuntu/disks/root.disk ro

With a "Z" not an "X."

That took care of my problem! I was able to boot immediately.

As for what your hard drive is called...you can run the Ubuntu Live CD, run gparted under sudo, and it will tell you the "/sda1" or whatever your drive is named. Mine happens to be /sda2.

Hope this helps!

---

