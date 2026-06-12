---
title: "grub configuration trouble 'en masse'"
date: 2010-12-04
forum: General Help
---

### Post by owners4life5 on 2010-12-04
Oh, boy this is going to take a while...before you read this, though, check out **[THIS]("http://ubuntuforums.org/showthread.php?t=1635687")** , that way you.ll have a general understanding of what exactly is going on. i have lucid, maverick, and xp all on one machine.

so after i installed xp and fixed my grub problem, it is very, very messy. let me explain, and draw a sort of "figure", if you will.

when i first boot my computer, i enter my BIOS p/w, and it brings me to a screen saying this:

```
GRUB Loading stage1.5.


GRUB loading, please wait...
Press 'ESC' to enter the menu... 1
```

if i don.t hit escape, it takes me directly to maverick. if i hit escape, it takes me to a screen like this:

```
Chainload into GRUB 2
________________________________________________________________
When you have verified GRUB 2 works, you can use this command to complete the upgrade:  upgrade-from-grub-legacy
________________________________________________________________
Ubuntu 10.10, kernel 2.6.35-23-generic
Ubuntu 10.10, kernel 2.6.35-23-generic (recovery mode)
Ubuntu 10.10, kernel 2.6.35-22-generic
Ubuntu 10.10, kernel 2.6.35-22-generic (recovery mode)
Ubuntu 10.10, kernel 2.6.35-25-generic
Ubuntu 10.10, kernel 2.6.35-25-generic (recovery mode)
Ubuntu 10.10, kernel 2.6.35-24-generic
Ubuntu 10.10, kernel 2.6.35-24-generic (recovery mode)
Ubuntu 10.10, memtest 86+
```

when i select any of the maverick distros, it of course, takes me to maverick, memtest to memtest, i.m not sure what the 2 lines of text do (i.m scared to touch them, ha), but when i select 'Chainload into GRUB 2', it takes me to this:

```
maverick 2.6.35-23-generic, with Linux vga=786  quiet splash
Ubuntu, with Linux vga=786  quiet splash (recovery mode)
maverick 2.6.35-22-generic, with Linux vga=786  quiet splash
Ubuntu, with Linux vga=786  quiet splash (recovery mode)
maverick 2.6.35-25-generic, with Linux vga=786  quiet splash
Ubuntu, with Linux vga=786  quiet splash (recovery mode)
maverick 2.6.35-24-generic, with Linux vga=786  quiet splash
Ubuntu, with Linux vga=786  quiet splash (recovery mode)
Windows NT/2000/XP (loader) (on /dev/sda2)
Ubuntu, with Linux 2.6.32-26-generic (on /dev/sda5)
Ubuntu, with Linux 2.6.32-26-generic (recovery mode) (on /dev/sda5)
Ubuntu, with Linux 2.6.32-25-generic (on /dev/sda5)
Ubuntu, with Linux 2.6.32-25-generic (recovery mode) (on /dev/sda5)
Ubuntu, with Linux 2.6.32-21-generic (on /dev/sda5)
Ubuntu, with Linux 2.6.32-21-generic (recovery mode) (on /dev/sda5)
```

when i select the first ubuntu/maverick options, they take me to maverick, the Windows option takes me to XP, and the bottom ubuntu options take me to lucid.

of course, this is feasible, i suppose, but it is rather annoying. is there any possible way i can make it to where it is something like this, and just select at startup?

```
Ubuntu Lucid
Ubuntu Lucid (recovery mode
Ubuntu Maverick
Ubuntu Maverick (recovery mode)
Windows XP
memtest86+
```

it doesn.t have to be exactly like that, i.m not even sure if that is possible (maybe it is.)

anyway, nothing extremely urgent, but i would like to fix asap.

thanks in advance,

---

### Post by owners4life5 on 2010-12-05
bump

---

### Post by owners4life5 on 2010-12-10
bump

---

### Post by oldfred on 2010-12-10
You are running with grub legacy (0.97) but have the upgrade to grub2 showing its menu if you select that. If it works, you should run the recommended command.

upgrade-from-grub-legacy

I also thought the vga=XXX option was obsoleted in grub2 and gave some boot issues. 
vga=799 is a deprecated boot option
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/454993](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/454993)

It looks like you have two different partitions with Ubuntu. You can houseclean some older kernels, but we recommend you keep the current one plus one older that you know works, just in case.

Check current kernel:
lsb_release -a
Go to Synaptic Package Manager and search for linux-image.
More info in post #8
[http://ubuntuforums.org/showthread.php?t=1283521](http://ubuntuforums.org/showthread.php?t=1283521)


Also to understand more about grub2.
General info:
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
[http://www.gnu.org/software/grub/manual/](http://www.gnu.org/software/grub/manual/)
The Grub 2 Guide (formerly Grub 2 Basics)
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202]("https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202")

---

