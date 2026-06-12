---
title: "Did I install this correctly? (on raid 0)"
date: 2011-07-01
forum: General Help
---

### Post by ericsoderstrom on 2011-07-01
Hi,

First off, a disclaimer: I know nothing at all about ubuntu, and know very little about computers in general =(

So I've been trying to install ubuntu 11.04 on my laptop, which is a sony vaio z with raid 0. Evidently raid 0 poses some sort of problem to ubuntu.

This is what I did:

Defragmented and shrank my windows partition
downloaded and burned the alternate install cd for ubuntu
booted from the alternate install cd
selected 'recognize raid' ... or some such thing when prompted during installation
selected something along the lines of 'install in largest contiguous free space' when asked where to install (my other choices seemed to be writing over an entire disc, which seems bad if I want to preserve windows 7)
I was then asked where to install grub, and got confused. So I entered the recovery shell (busybots?), checked the contents of dev/mapper, and told grub to install to the first directory I found there, which happened to be dev/mapper/isw_gfcbaifgj_Volume0.  I chose this pretty much arbitrarily

I'm now able to boot from either windows 7 or ubuntu... everything seems to work ok as far as I can tell. My questions are these:

1. Did I do anything grossly incorrect in my attempt to dual boot ubuntu?
2. Was installing the boot loader to dev/mapper/isw_gfcbaifgj_Volume0 a bad idea? Have I catastrophically destroyed something?
3. When I check my hard drive partitions, I now have two new ones. Neither of them are named. I expected to see only one new partition named 'ubuntu' ... or something like that. Why are there two, and why do they not have names?


Again, my apologies for my lack of computer savviest. Any help at all would be appreciated.

---

### Post by gordintoronto on 2011-07-01
It sounds like you can boot either Windows or Ubuntu. Congratulations!

I don't know enough to comment on the /dev/mapper/isw....

If you run Accessories/Terminal and enter the command:
fdisk -l
(that's the letter l, not a number) it will list your partitions. Perhaps there is a small swap partition. (Windows uses a swap file, but Linux uses a swap partition.) It's quite normal for Linux paritions to have no name other than, for example, /dev/sda1

---

