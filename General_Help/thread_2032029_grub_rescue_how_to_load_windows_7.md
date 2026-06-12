---
title: "grub rescue how to load windows 7"
date: 2012-07-22
forum: General Help
---

### Post by nazar2nirvana on 2012-07-22
i have installed windows 7 in my 1st partition and ubuntu in my 4th partition. i was doing some partition managing stuff. now i have 
"grub rescue> " when i boot on my laptop.

previously i used to face same problems but then i used to load windows 7 from grub rescue like:
root (hdX,X)
chainloader +1
boot

or something like that ...

now how can i do it

on doing "ls " on grub my windows 7 partition is "msdos1"
so 

set prefix=(hd0,msdos1)

"NOW HOW CAN I LOAD WINDOWS 7 WHAT IS NEXT LINE COMMAND"
ANY HELP????

---

### Post by oldfred on 2012-07-23
If grub from MBR cannot find grub files in Ubuntu or boot partition this may work:

grub > chainloader (hd0,1)+1
grub > boot

But generally you want to boot grub.

Grub Rescue Prompt Megathread - drs305
[http://ubuntuforums.org/showthread.php?t=1594052](http://ubuntuforums.org/showthread.php?t=1594052)
HOWTO: Boot & Install Ubuntu from the Grub Rescue Prompt 
[http://ubuntuforums.org/showthread.php?t=1599293](http://ubuntuforums.org/showthread.php?t=1599293)

You can install the Windows boot loader to the MBR temporarily or use Supergrub to boot a bootable system when grub is not working.

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)
[http://www.supergrubdisk.org/wiki/Main_Page](http://www.supergrubdisk.org/wiki/Main_Page)
[http://www.supergrubdisk.org/wiki/AutoSuperGrubDisk](http://www.supergrubdisk.org/wiki/AutoSuperGrubDisk)
Howto: Easy GRUB Bootloader Repair Windows,unetbootin, Supergrub 2008
[http://ubuntuforums.org/showthread.php?t=690912](http://ubuntuforums.org/showthread.php?t=690912)
Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10 - grub2) - talsemgeest
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)
Reinstall grub2 - Short version & full chroot version
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2)

---

### Post by OM55 on 2012-07-23
Here is a simple step by step solution to your problem:

Symptom:
========
After boot we get the prompt:

error: file not found.
Grub rescue>-


Problem:
========
The grub information on disk has been corrupted and the system can not boot from the proper partition

Solution:
=========
1. Boot with Ubuntu Live CD

2. Open terminal (command prompt)

3. Type: sudo fdisk -l

You will get a list of partisions, similar to the following list:

/dev/sda1 13 102400 de Dell Utility
/dev/sda2 * 13 1926 15360000 7 HPFS/NTFS
/dev/sda3 1926 30892 232676566 7 HPFS/NTFS
/dev/sda4 30893 60802 240245761 5 Extended
/dev/sda5 30893 59584 230467584 83 Linux
/dev/sda6 59585 60802 9777152 82 Linux swap / Solaris 

Ubuntu partition is the one with the name "Linux" (not necessarily the one with the star, although could be).
On this case is on '/dev/sda5' so we have to mount it:

4. sudo mount /dev/sda5 /mnt
   (replace 'sda5' with the partition name in your case)

5. And then install grub:
   sudo grub-install --root-directory=/mnt /dev/sda

6. Reboot and verify that all is working fine.

---

