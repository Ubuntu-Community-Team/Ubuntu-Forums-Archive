---
title: "unusual grub minimal bash-like line editing is supported, anyone can assist?"
date: 2011-03-21
forum: General Help
---

### Post by smouser on 2011-03-21
Hi Guys,
Ubuntu didn't start up all of a sudden. It got error and stuck at :   Minimal BASH-like line editing - Ubuntu Forums. I tried many ways   suggested to go into menu mode but failed.
I followed online solutions.. but none of them helped. I tried to list all partitions and I got this:
ls
(memdisk), (hd0), (hd0,msdos), (fd0)
i tried 
root (hd0)/boot , it said unknown filesystem
root (hd0,msdos)/boot, but it's a windows partition
root (f0)/boot, it said read error

The setup is dual boot with wubi, so i logged on to windows7 and   installed partition magic, but i couldn't see the linux parittion, the  whole harddisk is 500G, but only 2xxG is visible in NTFS

I used liveCD to boot the system, but when i run sudo fdisk -l, i didn't see anything

I have no idea why it happened, and the last successful log on was in Ubuntu, so i doubt it's due to windows update..

I am going to try Solution #1 (10.04) in wubi megathread.

Can anyone suggest what has actually gone wrong? WIll i able to recover   the data in my linux parition given partition magic cannot see it?

THanks!

---

### Post by bcbc on 2011-03-22
This is a very common problem with 10.04 as shown by the popularity of the wubi megathread. It also mentions a tool that you can use to access the virtual partition used by Wubi (this is why you can't find it because it's not a real partition). It's a file C:\ubuntu\disks\root.disk (change C: depending on the drive you installed on but it seems like C: from the ls output). 

And PS that should probably be (hd0,msdos1)

So you can just enter:
```
linux /vmlinuz root=/dev/sda1 loop=/ubuntu/disks/root.disk ro quiet splash
initrd /initrd.img
boot
```
And that should boot it. Then you can apply the Permanent Fix shown in the thread.

---

### Post by smouser on 2011-03-22
Ok will try. THanks!
just to confirm, ONLY type the following in GRUB prompt will be sufficient to bring me into Ubuntu?

linux /vmlinuz root=/dev/sda1 loop=/ubuntu/disks/root.disk ro quiet splash
initrd /initrd.img
boot

---

### Post by bcbc on 2011-03-22
> **smouser said:**
> Ok will try. THanks!
just to confirm, ONLY type the following in GRUB prompt will be sufficient to bring me into Ubuntu?

linux /vmlinuz root=/dev/sda1 loop=/ubuntu/disks/root.disk ro quiet splash
initrd /initrd.img
boot

Yes... that will work. Note it's based on your reported output of "ls" - that it only showed the single partition (hd0,msdos1)

---

### Post by smouser on 2011-03-22
Correction:
when i did ls it gave
(memdisk) (hd0) (hd0,msdos1) (fd0)
when i did ls -la it gave
device memdisk: filesystem type tarfs
device hd0: partition table
     Partition hd0,msdos1, File system type ntfs, UUID xxxxxx
device fd0: uknown filesystem

I type the command bcbc suggested but i got error: file not found

In fact, i cannot see c:\ubuntu\winboot\wubildr in windows.

Then i followed anohter instructions..
Boot using a live CD
sudo fdisk -l
sudo mkdir /win
sudo mount /dev/sdxy /win
sudo mkdir /vdisk
sudo mount -o loop /win/ubuntu/disks/root.disk /vdisk

It failed in the last line, saying the root.disk is not found

I searched some more posts and realized my root.disk is missing. In fact, I dont have c:\ubuntu\disks!

Then i ran chkdsk and hoped the file would be recovered but it didn't!!!

Looks like i can never recover my ubuntu...

Remember a few times my ubuntu hung and i coudln't log off, i ran init 6 in terminal, would it be the cause?

---

### Post by bcbc on 2011-03-22
That's not good ... just make sure they're not sitting in a hidden C:\FOUND.000 folder. Look based on size as well as name. 

Not sure what causes this, but the root.disk is a large file and when Ubuntu hangs it may be a sign of corruption which can be compounded by hard shutdowns etc. You can use Alt+SysRq REISUB instea

---

### Post by smouser on 2011-03-22
Not able to find it anywhere.. i can't find c:\found.000, nor root.disk anywhere. Is there anyway i can find big files in windows? I know I can do it in with linux commands
Probably my last resort is to re-install. But what is surprising is i cannot get back my data. I think creating a separate partition is safer instead of having a file that can be removed by mistake and causing loss of entire drive.
Anyway thanks for your assistance bcbc.

---

