---
title: "cannot mount usb devices (automatically OR manually)"
date: 2010-10-30
forum: General Help
---

### Post by talvikki77 on 2010-10-30
Hi people.

For some reason, my computer suddenly stopped being able to mount usb devices (flash drives and USB mouse).

I have Hardy Heron on a Thinkpad z60t. I'm trying to upgrade to Lucid Lynx but I don't have enough space on my computer, so I'm trying to delete stuff from the Windows partition right now.. Anyway, the flash drives were working fine until today. I may have accidentally unplugged a flash drive without unmounting it..I thought the computer was turned off but actually it was hibernating. But this flash drive still works on a (different) Windows machine, and I can't mount ANY flash drives on Ubuntu, not just the one I removed improperly.

Here is what I have tried so far:

-Went into Synaptic and made sure that usbmount was installed.

-Checked that automount and automount_open were checked in Nautilus.

-Restarted the computer about ten times. (The other thing that sometimes works is waiting a few days and trying again, but I would really like to use my flash drive tonight >.<)

-Tried to mount the flashdrive manually in a variety of different ways, including forced.

One problem is that I can't even figure out where my flash drive is. The two commands I found online were sudo fdisk -l and lsusb, but neither has given me any useful information. The Thinkpad is kind of tied up right now but I'll try to get the exact infos on here later.

Basically, sudo fdisk -l tells me I have sda1, sda2, sda3, sda4 and sda5. I believe sda1 was Linux, sda2 was NTFS, sda 3 was something like "extended", sda4 was FAT and sda is swap.

lsusb tells me there are 5 ports but doesn't give any useful information (like names of devices).

I have tried mounting each of the drives listed by fdisk as well as /dev/sbd1 where I assumed the flash drive might be hiding, but none of that has worked. Some of those drives are (obviously) other things like my file system, some of them are emtpy, and /dev/sdb1 apparently doesn't exist.

If you have some suggestions, please please please be very literal and exact about what I need to do. I'm not a newbie to Ubuntu or the command line but I don't use the terminal or any of the system stuff very often, so you will have to tell me exactly what to click on and/or type in.

Edit: Resolved..it just started working again, no apparent rhyme or reason.

---

