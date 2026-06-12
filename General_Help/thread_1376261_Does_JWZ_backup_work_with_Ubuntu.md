---
title: "Does JWZ backup work with Ubuntu?"
date: 2010-01-09
forum: General Help
---

### Post by WayneSchuller on 2010-01-09
hi,

I've been using JWZ backup for a number of years.
[http://jwz.livejournal.com/801607.html](http://jwz.livejournal.com/801607.html)

It is basically a way of using rsync to nightly mirror your main hard drive to a second one. JWZ uses a mac, but I thought it should work similarly on linux.

I have a very simple system - everything in on root partition - ubuntu karmic is my only system.

Today I removed the primary backup hdd, plugged the backup in where it belonged. But it wouldn't boot.

Using the livecd I had two ideas to make it work:
1. Change the drive label from /mirror to /
2. Use fdisk to make the partition set as 'boot'.

This still didn't work.

I had to go through all sorts of grub-rubbish to get it to work.

Eventually I found that from the live cd could be used to update the MBR on the new main hdd:
grub-install --root-directory=/media/root/boot /dev/sda

But this only gave me a grub command line.

I then had to follow all sorts of grub buffoonery from [http://help.ubuntu.com/community/Grub2](http://help.ubuntu.com/community/Grub2) to boot into the system. Even now I am not sure it is fixed if I reboot.

Is there a trick to getting the JWZ rsync backup mirror system to work on Ubuntu?

I like the system because I thought it would just allow me to boot off the mirror backup anytime.

Please advise?

---

