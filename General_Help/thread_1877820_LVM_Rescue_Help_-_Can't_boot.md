---
title: "LVM Rescue Help - Can't boot"
date: 2011-11-08
forum: General Help
---

### Post by tonyferrari on 2011-11-08
Hi Gang,

I've done something stupid...closed my laptop lid while doing an apt-get upgrade. Well, it was late at night and I was falling asleep on my laptop. Anyways, when I boot now, I get the "The disk drive for / is not ready yet or not present" and it dumps me into single user mode or some rescue mode. 

Now when I first installed Ubuntu 10.04 desktop 64-bit, I did the default install. So my main partition should be one big LVM volume with root et al stuck in there. 

So I next booted off of a live Ubuntu CD to attempt a rescue. When I run fdisk -l it still sees my partitions:

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0009cf3f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   569539157   284768555   83  Linux
/dev/sda2       960167934   976773119     8302593    5  Extended
/dev/sda5       960167936   976773119     8302592   82  Linux swap / Solaris


When I run pvscan it says "No matching physical volumes found".
I initially installed lvm2 as follows...
sudo -i
apt-get install lvm2

And then ran these commands:
modprobe dm-mod
vgchange -a y

Still nothing. It's not finding the VolumeGroup config info I think. 

I tried to extract the lvm configuration file from the beginning of the partition with:
dd if=/dev/sda1 bs=512 count=255 skip=1 of=/tmp/lvm.txt

When I look at lvm.txt I'm seeing binary data of course but no lvm config data.

What am I doing wrong? Is my data hosed? What else can I do?

Thanks for any tips you can give.

Cheers,

Tony

---

