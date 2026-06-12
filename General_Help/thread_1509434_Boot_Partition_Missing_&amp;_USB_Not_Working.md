---
title: "Boot Partition Missing &amp; USB Not Working"
date: 2010-06-14
forum: General Help
---

### Post by MsEvette on 2010-06-14
I am a newbie to Linux/Ubuntu. Apparently I altered my partitions while  trying to make room for Ubuntu 10.04, and now I'm in a mess. For two weeks I have been searching the forums for a solution only to find  instructions I don't understand or partial solutions.

Here's my situation.

I have an Acer AspireOne netbook (no CD, only USB).

I am able to access F2 setup, so I can prioritize the boot order. I can  position my bootable  (ubuntu-10.04-netbook-i386.iso) usb drive at the  top of list, but when my computer reboots via usb, there's just a black  screen with a white dash in the upper left corner that flashes. 

When I boot with the hard drive I get:
error: no such partition.
grub rescue>

So far, the only commands I have found that work are:

grub rescue>ls
(hd0) (hd0,3) (hd0,2) (hd0,1)

grub rescue>set
prefix=(hd0,5)/boot/grub
root=hd0,5

Now, like I said, I'm a newbie. But that hd0,5 concerns me; doesn't seem  to fit.

I'm not concerned with saving data. I'm willing to start from scratch. I  just can't get past that grub rescue prompt and I can't access my usb  port so that I'm able to run the LiveCD.

PLEASE HELP!

---

### Post by FORRES on 2010-06-15
Well if you dont care about loosing your data, just take out the physical disk out of your PC, connect it to another PC (Internally or USB), and format it.
Then, you can start from scratch!:p

GL!

---

