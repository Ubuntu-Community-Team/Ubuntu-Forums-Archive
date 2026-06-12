---
title: "Ubuntu only boots when live cd usb is connected"
date: 2012-05-29
forum: General Help
---

### Post by private54321 on 2012-05-29
I'm new to Ubuntu and i have this weird problem.

Every time i start my pc it goes to the Grub console loader ( i disable the graphical as it was causing problems) well there are like 5 options.
2 of vista, 1 of memory, and 2 of Ubuntu that ends in generic-pae (one is recovery mode).
Everytime i click on the generic-pae one without having the usb that i used to install Ubuntu trough Live CD it crashes, when i put it back on i repeat the steps and it boots to Ubuntu without problems. 

Is Grub detecting my Ubuntu Live CD USB as a boot option? :(

Please help me. :P

Edit: forgot 1 of the boot options is boot previous linux version, not the memory thingy i said earlier.

---

### Post by gnusci on 2012-05-29
Post the output of the following command:

$ cat /etc/fstab

---

### Post by private54321 on 2012-05-29
> **gnusci said:**
> Post the output of the following command:

$ cat /etc/fstab

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=f9c4c7e1-93f8-4ed1-b9a1-792be9a5c205 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=c7bba28d-6cd5-4bdb-83a4-6ffff4e3e6b0 none            swap    sw              0       0

---

### Post by private54321 on 2012-05-29
> **gnusci said:**
> Post the output of the following command:

$ cat /etc/fstab

you still here? :p

---

### Post by wilee-nilee on 2012-05-29
There is a tool that can repair and provides a debug script as well, here is the link to it.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

You can use a live ubuntu cd/usb flash to run it or in a ubuntu install, or download the cd, there is a recommended repair that works for basic reloads of the mbr.

Run the boot summary and post the url address in the thread, some suggest running the script first before try the recommended repair it is your call.

If you are actually getting to the install desktop you can reload the mbr from there through a terminal. 

You would run this command to identify the HD first.

```
sudo fdisk -lu
```Once you know the HD this command reloads the mbr

```
sudo grub-install /dev/sdX
```The X is as your HD reads, if it is sda, the X would be an a, no partition numbers, if the HD is sdb, the X is a b

Last command.

```
sudo update-grub
```You are welcome to just post the script for more concise instructions.

---

### Post by private54321 on 2012-05-29
> **wilee-nilee said:**
> There is a tool that can repair and provides a debug script as well, here is the link to it.

here you go

[http://paste.ubuntu.com/1012713/](http://paste.ubuntu.com/1012713/)

---

### Post by private54321 on 2012-05-29
i should also add that when i unplug the usb (it's 1.5GB). the whole os crashes.

---

### Post by wilee-nilee on 2012-05-29
So the pendrive is reading as sda, and the hard drive as sdb, it looks like you are in the install.

Grub is in the sdb master boot record, but you have disabled some of grub.

You might just fix it with this command in the installs terminal.

```
sudo update-grub
```If that does not do it reload the mbr with.

```
sudo grub-install /dev/sdb
```Then run the grub-update command above it.

You want to run this command to confirm the HD is still sdb

```
sudo fdisk -lu
```These commands may get you fixed, but since you have modified grub it might take a purge and reload of grub, post where you are at after you try these commands.

When you are in the install make sure the usb is unplugged as well. YOU wrote the last post while I was posting this so, it is strange that Ubuntu would crash with just a removal of the thumb.

---

### Post by private54321 on 2012-05-29
> **wilee-nilee said:**
> 

You might just fix it with this command in the installs terminal.

```
sudo update-grub
```

I ran that command then i re-booted the pc without the USB and it boot Ubuntu fine.

Guess that fixed it but just incase this is what i get when i type **sudo fdisk -lu**

```
   Device Boot      Start         End      Blocks   Id  System
/dev/sde1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sde2          206848   383537151   191665152    7  HPFS/NTFS/exFAT
/dev/sde3       383539198   488396799    52428801    5  Extended
/dev/sde5       383539200   390537215     3499008   82  Linux swap / Solaris
/dev/sde6       390539264   488396799    48928768   83  Linux
victor@victor-desktop:~$ 

```

is everything fine now? :p 

thanks for your help, it means a lot.:KS

---

### Post by wilee-nilee on 2012-05-29
> **private54321 said:**
> I ran that command then i re-booted the pc without the USB and it boot Ubuntu fine.

Guess that fixed it but just incase this is what i get when i type **sudo fdisk -lu**

```
   Device Boot      Start         End      Blocks   Id  System
/dev/sde1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sde2          206848   383537151   191665152    7  HPFS/NTFS/exFAT
/dev/sde3       383539198   488396799    52428801    5  Extended
/dev/sde5       383539200   390537215     3499008   82  Linux swap / Solaris
/dev/sde6       390539264   488396799    48928768   83  Linux
victor@victor-desktop:~$ 

```is everything fine now? :p 

thanks for your help, it means a lot.:KS

I'm not sure why the HD is reading as sde now but if your up and running I think you're okay, there are others that are really experienced in this area, so they may comment if they see any problems.

You are aware of the boot-repair tool now if you were not before it is rather helpful. ;)

Just remember that most grub adjustments are followed by the update-grub command to get everything written correctly.

---

### Post by private54321 on 2012-05-29
> **wilee-nilee said:**
> I'm not sure why the HD is reading as sde now but if your up and running I think you're okay, there are others that are really experienced in this area, so they may comment if they see any problems.

You are aware of the boot-repair tool now if you were not before it is rather helpful. ;)

thanks man, i'll just run it like it is right now and bump the thread if a problem re-occurs.

yes, that tool is very handy. :D

if you don't mind answering this question. Are video drivers installed already because i downloaded ones from nvidia for linux but don't know if  i should run them? 

also additional drivers show something about no proprietary drivers are use in this system.

---

### Post by wilee-nilee on 2012-05-29
> **private54321 said:**
> thanks man, i'll just run it like it is right now and bump the thread if a problem re-occurs.

yes, that tool is very handy. :D

if you don't mind answering this question. Are video drivers installed already because i downloaded ones from nvidia for linux but don't know if  i should run them? 

also additional drivers show something about no proprietary drivers are use in this system.

I'm not real up on nvidia, or graphic drivers at all really, but I have seen advice that using the drivers straight from nvidia are not to be used unless they are your only choice. If it looks good the install found what you needed in the repos.

Basically with the straight from nvidia they don't follow some sort of updates and upgrades not sure of the specificities here though.

---

