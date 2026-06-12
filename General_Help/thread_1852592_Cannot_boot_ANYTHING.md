---
title: "Cannot boot ANYTHING"
date: 2011-09-30
forum: General Help
---

### Post by spacetimecowboy on 2011-09-30
Hi there,
 
My friend was using my Acer Aspire One netbook running Ubuntu 10.04.
 
There was some kind of crash with a frozen screen and now the machine won't boot, it spews out a lot of code... seems to be trying to mount core files, but can't find the directories 
 
eg 
 
Killed mount: mounting /dev on /root/dev failed: No such file or directory mount: mounting /sys on /root/sys failed: No such file or directory mount: mounting /proc on /root/proc failed: No such file or directory Target filesystem doesn't have /sbin/init. No init found. Try passing init= bootarg. BusyBox v1.13.3 (Ubuntu 1:1.13.3-1ubuntu11) 
 
I have tried booting various versions of Ubuntu from USB and it reaches the menu but can't do much else, some code repeadedly referencing "casper" (sorry not more specific right now)
 
The Ubuntu 10.04 Rescue Remix returns simply:
 
"Could not find ramdisk image: /casper/initrd.lz
boot:"
 
No idea where to go from here.
 
Thank You!!!!!!!!!!!!!!!!!

---

### Post by CHEWS on 2011-09-30
if it installed on harddisk hold escape to show grub boot menu select ubuntu recovery console tell me if that boots if so I can help

---

### Post by spacetimecowboy on 2011-09-30
Hi,
 
Rescue not installed on Hard disk, attempting boot from USB.
 
Holding escape has no function.
 
 
?
 
Thanks

---

### Post by CHEWS on 2011-09-30
its probably a bad usb image or iso if it not a hardrive installation your trying to fix.

---

### Post by seawolf167 on 2011-09-30
> **CHEWS said:**
> if it installed on harddisk hold escape to show grub boot menu select ubuntu recovery console tell me if that boots if so I can help

Hold the ***[SHIFT]*** key, not escape.

Can you post the error messages received verbatim please?

---

### Post by spacetimecowboy on 2011-10-01
UPDATE

Have managed to boot 9.10 from USB, but hard drive data cannot be copied as i don't have the permissions.

How to overcome?

I will start a new thread and post it here.

Many thanks all.

---

### Post by spacetimecowboy on 2011-10-01
[http://ubuntuforums.org/showthread.php?p=11301912#post11301912](http://ubuntuforums.org/showthread.php?p=11301912#post11301912)

---

### Post by spacetimecowboy on 2011-10-01
For more information,
 
Booting Ubuntu Rescue Remix version 10.04 from USB I got welcome text  followed by
 
**For the default live system, enter "live". To Run memtest86+, enter  "memtest"**
 
Then the command line,
 
**boot: _**
 
Entering the command "**live**" returns;
 
**Could not find ramdisk image: /casper/initrd.lz**
**boot: _**
 
Starting without USB in gives me loads of stuff like...
 
**[ 1.138876] [ <c0221273> ] ? get_fs_type+0x33/0xb0**
 
that I would love to not type out if possible, followed by...
 
**Killed**
**mount: mounting /dev on /root/dev failed: No such file or  directory**
**mount: mounting /sys on /root/sys failed: No such file or  directory**
**mount: mounting /proc on /root/proc failed: No such file or  directory**
**Target filesystem doesn't have /sbin/init.**
**Nop init found. Try passing init= bootarg**
 
**Busybox v1.13.3 (Ubuntu 1:1.13.3-1ubunut11) built-in shell (ash)**
**Enter 'help for a list of built in commands.**
 
**(initramfs) _**
 
I can type out the long list of commands availiable from "**help**" if  neccecary.
 
Thanks for your attention.

---

### Post by seawolf167 on 2011-10-01
See if [this page]("https://help.ubuntu.com/community/BootFromUSB#Using_an_internal_hard_drive") helps/gives you any ideas as how to proceed.

---

### Post by javacookies on 2011-10-17
I also experienced this. Now I can't boot to any Ubuntu I installed on different HDDs. I can't even boot to recovery mode. Even Alt+sysrq+reisub won't work to restart whenever the system hangs......I'm in vain please help me :(

---

