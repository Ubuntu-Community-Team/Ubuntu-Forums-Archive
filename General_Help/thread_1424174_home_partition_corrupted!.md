---
title: "/home partition corrupted!"
date: 2010-03-07
forum: General Help
---

### Post by sensay on 2010-03-07
Relevant Info:

[B]320GB seagate sata drive, 290GB partition for /home, 25GB partition for / and the rest for swap.

Ubuntu 9.04 Fresh Install.[/B]

My power supply died today, in the process of that happening my hard drives seem to have become corrupted.

After replacing the PSU I couldnt access ubuntu so i booted with a live CD. When i tried to mount the partitions i got Mount Failed.

I reinstalled ubuntu but when it came to selecting the partitions i could not mount my /home partition. If i tried i got an error stating that one or more installation files could not be removed. I reinstalled without the /home partition and it was fine.

On my fresh install now and i still get the mount failed message when trying to access the drive. It says to try dmesg | tail for more info, which i have done.

```
jay@Ifrit:~$ dmesg | tail
[   38.736631] ISO 9660 Extensions: RRIP_1991A
[   39.160511] eth1: no IPv6 routers present
[  100.680743] ppdev0: registered pardevice
[  100.728619] ppdev0: unregistered pardevice
[  101.854404] ppdev0: registered pardevice
[  101.900022] ppdev0: unregistered pardevice
[  101.908980] ppdev0: registered pardevice
[  101.956162] ppdev0: unregistered pardevice
[  268.363754] EXT3-fs error (device sdb5): ext3_check_descriptors: Block bitmap for group 640 not in group (block 0)!
[  268.364148] EXT3-fs: group descriptors corrupted!
jay@Ifrit:~$ 
```I have also tried to run fsck. This also fails because it cant read the superblock, it suggest trying e2fsck -b <new superblock> <device> which i have also tried with no success.

Please help, all my media is on this drive and i cant afford to lose it! :sad:

---

### Post by lavinog on 2010-03-07
I don't know how to repair the drive exactly, but the testdisk package is very handy for this sort of stuff.
photorec (part of the testdisk package) can search the partition for all of your files and recover them...make sure you have a 2nd drive to save them to though.

Always have a backup plan...hard drives should be considered extremely fragile, and will pretty much fail when you least expect them to.

---

### Post by sensay on 2010-03-07
Hi, ive tried using testdisk and photorec just now. Photorec has a way to retrieve files from the hard drive i see but i only want avi files right now not EVERYTHING. There is an option to select what files will be saved and .avi is not there, its been running for a while now and now avis have been extracted either i dont think its gonna work. Any help?

EDIT: My second hard drive is now unmountable, it says Fuse:failed device is busy./ Nothing i can see is using the drive...

---

### Post by sensay on 2010-03-07
Hmm, i seem to have a load of mpeg files now, ive never downloaded an mpeg before. I just played one and they are scrambled bits of my video collection. If this is file recovery its ridiculous i cant do anything with these, each episode is broke up into loads of parts that are mainly glitch effects with milliseconds of real picture.

There has to be a better way, please!

---

### Post by sensay on 2010-03-08
[SIZE=6][SIZE=3]Bump![/SIZE]
[/SIZE]

---

### Post by sensay on 2010-03-08
I used photorec again to try and recover the family pictures from the partition, somehow it managed to recover 17000 jpeg files and they were nearly all from my internet temp folder, not a single of MY pictures was found.

I'll be heartbroken if i lose those too, i know i should have backed up but thats all the pictures of my baby boy on there. If anyone has any other advice on what to do please post, im going nuts here!

---

### Post by sparky-steve on 2010-03-08
Hi Sensay

I've no user-help to give you right now, but I read your post and thought I'd chime in, because I've also lost baby photos before.

First and foremost, whatever you continue to try, only mount it read only.

The point I want to make is that when everything user-land fails, you can STILL send the drive away to a data recovery specialist; they charge alot, but it really depends on what value you give the data.

I believe they physically disassemble the drive, platter by platter, and retrieve everything they can.

On the drive I had done, they recovered almost everything. It did cost me, but for me it was worth it.

Dont give up just yet.... Find a data recovery company near to you, and have a word.

SS

---

### Post by lavinog on 2010-03-08
Is your drive making any funny noises?

Since your other drive doesn't seem to be working, I am wondering if your controller is damaged.
Is this SATA or IDE?
Power supply failures can typically damage other components
I would pull out the drive you want to recover, get a usb adapter for it.
Get your computer in working order, and recover your drive using the usb adapter You don't want to be using that drive for anything. If you are booting off of that drive, and the drive is deteriorating, continued use is going to make further recovery more difficult.

---

