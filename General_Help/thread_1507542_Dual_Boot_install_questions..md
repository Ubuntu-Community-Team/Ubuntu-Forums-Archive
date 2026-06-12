---
title: "Dual Boot install questions."
date: 2010-06-11
forum: General Help
---

### Post by Hexeir on 2010-06-11
I am attempting to install Ubuntu 10.04 side by side with my existing XP on my Sony Vaio. Since I am using NTFS, how to I go about making a partition so that I can install Ubuntu?

---

### Post by spiky001 on 2010-06-11
when yo get to the partion option dose it give you the option to install side by side or have you not got that far yet?

---

### Post by JayKay3000 on 2010-06-11
Ubuntu allows you to install it using an application called Wubi that comes with it. You can install it inside windows as an application. It will look, feel and work like it's on a partition but you will be able to get rid of it using add/remove programs in windows.

There are some applications that allow you to re-size your hard drive, else to partition you will probably have to erase xp so that you can make the partitions. 15 - 20 gb is more than plenty for an ubuntu partition

You can simply make a new blank partition and install ubuntu on that using the cd. If you install it on a blank partition then it will find and add windows to the boot loader so you will be able to choose between the two at startup. (Installing it via wubi will do a similar thing)

If you need more detail then shout!

But that's pretty much the basics.

---

### Post by X-Windows on 2010-06-11
I wrote a how-to here that may help, although that was for a clean install of both.[http://ubuntuforums.org/showthread.php?p=9343022](http://ubuntuforums.org/showthread.php?p=9343022)

 To create space for ubuntu, in gparted select your partition and shrink it to whatever size you need, then proceed.

---

### Post by garvinrick4 on 2010-06-11
Get into your XP install and DEFRAG at least 2 times before making another partition for Ubuntu. If you can make your partition in program gparted in live cd before you install.
Google gparted and read instructions. Also read about primary, extended and logical partitions. It is not really very hard but you must understand before you use manual partitioning. If you choose side by side in Ubuntu install it will do it for you and split the drive 50/50. If that is fine with you then all is well. Still read all you can on drive partitioning it will come in very handy as you grow in Linux.

---

### Post by garvinrick4 on 2010-06-12
> **JayKay3000 said:**
> Ubuntu allows you to install it using an application called Wubi that comes with it. You can install it inside windows as an application. It will look, feel and work like it's on a partition but you will be able to get rid of it using add/remove programs in windows.

There are some applications that allow you to re-size your hard drive, else to partition you will probably have to erase xp so that you can make the partitions. 15 - 20 gb is more than plenty for an ubuntu partition

You can simply make a new blank partition and install ubuntu on that using the cd. If you install it on a blank partition then it will find and add windows to the boot loader so you will be able to choose between the two at startup. (Installing it via wubi will do a similar thing)

If you need more detail then shout!

But that's pretty much the basics.
Use the uninstall inside of WUBI folder in C: drive right next to USERS named UBUNTU.
Sometimes when you uninstall from Add and Remove programs it leaves the wublder inside of the Windows boot manager and it gets a bit goofy on next install. This I have experienced not just read about. I keep one machine with a WUBI install inside of Vista just so others can use the machine and I can keep up with the WUBI experience. It can be deleted using a simple command in Windows.
```

bcdedit delete {indentifacation # with the wublder in it}
``` (including brackets)

This is for vista or 7.

---

### Post by veggen on 2010-06-12
You might as well use some Windows program for this task. I always use the old Partition Magic (but there must be a suitable free alternative) and just create a new partition from the free space on the existing one.

---

### Post by garvinrick4 on 2010-06-12
I enjoy using gparted to make my partitions or delete or resize or Label. I am not kidding when I say the package "gparted" will do everything but kiss you good night when you learn to use it.

---

