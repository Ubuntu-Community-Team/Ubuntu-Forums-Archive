---
title: "information recovery"
date: 2011-10-07
forum: General Help
---

### Post by pr3zident on 2011-10-07
Ok i have an old seagate drive that's been corrupt for years, but i just realized why not try to see if it works on linux,..
when i plug it in it doesn't connect but it lights up 
i opened the terminal up i tried "mount"
the drive didn't show up and then i tried lsub with the drive plugged in and plugged out when it was plugged it lsub showed the drive .... is there anyway i can get this drive to mount ? or possibly just retrieve all the information ?  

ubuntu 10.04

---

### Post by jazzon on 2011-10-07
If you are running default Ubuntu, install the package gparted.  USE IT TO LOOK AT THE DRIVE ONLY!!  Get us the filesystem type (NTFS, FAT, etc.), the number of partitions, and which partition is which filesystem type and more help will be available.

---

### Post by pr3zident on 2011-10-07
> **jazzon said:**
> If you are running default Ubuntu, install the package gparted.  USE IT TO LOOK AT THE DRIVE ONLY!!  Get us the filesystem type (NTFS, FAT, etc.), the number of partitions, and which partition is which filesystem type and more help will be available.

That's the thing it doesn't mount so its not showing up in gparted ..

this is what i see when i do lsusb 

Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 1934:0702  
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 004: ID 413c:8130 Dell Computer Corp. 
Bus 003 Device 003: ID 046d:0b05 Logitech, Inc. 
Bus 003 Device 002: ID 046d:c512 Logitech, Inc. LX-700 Cordless Desktop Receiver
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
**Bus 002 Device 035: ID 13fd:1617 Initio Corporation **
Bus 002 Device 021: ID 043d:0180 Lexmark International, Inc. 
Bus 002 Device 003: ID 03f0:1807 Hewlett-Packard 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 0c45:63e2 Microdia 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

The bold bus is the drive because when i unplug the drive that's what disappear..

---

### Post by jazzon on 2011-10-07
sorry so long to reply, dealing with an issue of my own im getting help on.

Hmmm...so it is usb recognized, but not fs recognized (or it would automount if your system allows it).

Suspect a bad partition table, or faulty communications chip on the drive.  Give me a few minutes to look around.  And i will get back to you.

By the way... If you insert a flash drive (thumb drive) or other USB memry device, does it auto mount and show up on the desktop?  (are you using GUI or CLI?)

---

### Post by pr3zident on 2011-10-07
> **jazzon said:**
> sorry so long to reply, dealing with an issue of my own im getting help on.

Hmmm...so it is usb recognized, but not fs recognized (or it would automount if your system allows it).

Suspect a bad partition table, or faulty communications chip on the drive.  Give me a few minutes to look around.  And i will get back to you.

By the way... If you insert a flash drive (thumb drive) or other USB memry device, does it auto mount and show up on the desktop?  (are you using GUI or CLI?)

Ok cool... yes if i insert a flash drive it is auto mounted and shows up on the desktop....

---

### Post by jazzon on 2011-10-07
dont mean to sound insulting here, but do you know how to use gparted?  It might not have shown in the default window since it was not drive0.  There is a drop down button to select the device in question.  Did you look for it in gparted or just the main window?

Also navigate to /dev/disk/by-id and see if it shows up there.  If it does then the comp knows its a drive which will be a pluss 1 for us.  If not then this gets harder.

---

### Post by jazzon on 2011-10-07
try running this from a command line and post output here

```
sudo fdisk -l
```Thats lower case L not 1 or lowercase I

---

### Post by pr3zident on 2011-10-07
> **jazzon said:**
> try running this from a command line and post output here

```
sudo fdisk -l
```Thats lower case L not 1 or lowercase I

ok cool yea i know how to use gparted and it is not showing up in devices either... and when i do fdisk -l nothing is showing up
and /dev/disk/by-id - its not showing up there either i tried with it plugged in and plugged out ...

---

### Post by jazzon on 2011-10-08
Sorry for long delay, i got side tracked.  
You've just taken this out of my league.  THis is either a drive which requires some kind of proprietary stuff, or it is truley dead.  Mind you I'm not an expert.

One other thing you could try that I know of is to boot with it plugged in, (if system freezes at bios turn it off till bios is done then plug it in before ubuntu boots) and run
```
dmesg | grep usb
``` and see if it is there as a block device assigned to a /dev.

If it is i can help you mount it, if not there is nothing more i can tell you.  Just reply to this post to keep it active so someone else will look at it.

---

### Post by pr3zident on 2011-10-08
> **jazzon said:**
> Sorry for long delay, i got side tracked.  
You've just taken this out of my league.  THis is either a drive which requires some kind of proprietary stuff, or it is truley dead.  Mind you I'm not an expert.

One other thing you could try that I know of is to boot with it plugged in, (if system freezes at bios turn it off till bios is done then plug it in before ubuntu boots) and run
```
dmesg | grep usb
``` and see if it is there as a block device assigned to a /dev.

If it is i can help you mount it, if not there is nothing more i can tell you.  Just reply to this post to keep it active so someone else will look at it.


Thanx anyway man I really appreciate the help ... I think the drive is just fried ill work @ it some more and hopefully someone replies and has an answer ... I also tried testdisk and photorec couldn't find the drive maybe its gone and I set my hopes to high :)

---

