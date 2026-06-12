---
title: "mount: mounting /dev  on /root/dev  failed"
date: 2011-05-06
forum: General Help
---

### Post by candtalan on 2011-05-06
I am suddenly getting boot failure. Using Ubuntu 10.04.2 this is a well established installation, and is used almost constantly.

The boot screens get past the grub choice list and then almost immediately show text which includes this

mount: mounting /dev  on /root/dev  failed: no such file
mount: mounting on /sys on /root/sys failed: no such file or directory

This 10.04.2 is on a hard drive and ther are other /Ubuntu versions also on this drive which boot normally - 10.10 and 11.04

So 
I guess that something has gone wrong with my 10.04.2

I tried several of the earlier kernels in the grub menu in the 10.04.2 but no good.

Help please??

tia

---

### Post by dino99 on 2011-05-06
and recovery mode fail too ? otherwise select "repair package", then watch the logs to know about this issue

---

### Post by candtalan on 2011-05-06
> **dino99 said:**
> and recovery mode fail too ? otherwise select "repair package", then watch the logs to know about this issue

Yes unfortunately Recovery mode gets only to the same (failed) place (in scripts??)

Seems like a very early-on problem here?

---

### Post by dino99 on 2011-05-06
then you may need to chroot it from an other distro or a livecd

follow this example:
[http://ubuntuforums.org/showthread.php?t=1263030&page=2](http://ubuntuforums.org/showthread.php?t=1263030&page=2)

when done, then remove/purge then reinstall grub-pc & grub-common from synaptic (check that menu.lst from grub1 is no more around as it conflict with grub2)

---

### Post by candtalan on 2011-05-06
> **dino99 said:**
> then you may need to chroot it from an other distro or a livecd

follow this example:
[http://ubuntuforums.org/showthread.php?t=1263030&page=2](http://ubuntuforums.org/showthread.php?t=1263030&page=2)

when done, then remove/purge then reinstall grub-pc & grub-common from synaptic (check that menu.lst from grub1 is no more around as it conflict with grub2)
Thanks. 

A question please: I know how to reinstall grub using a live CD (grub2) although the method I have used and am a bit familiar with does not use chroot methods - it just copies files from the CD I think. 
You say grub-pc and grub-common - is it essential I do those, or does the grub-install include those packages?

---

### Post by candtalan on 2011-05-06
Whoops. 
The live CD disc utility reports this partition (/dev/sda5)(ext4) as being NOT clean.
A live CD terminal trying to run

ubuntu@ubuntu:~$ sudo e2fsck -v /dev/sda5

returns an error as if the partition is busy or cannot be mounted

e2fsck 1.41.11 (14-Mar-2010)
e2fsck: Device or resource busy while trying to open /dev/sda5
Filesystem mounted or opened exclusively by another program?
ubuntu@ubuntu:~$ 

any comments please?
tia

---

### Post by candtalan on 2011-05-06
bump?

---

### Post by WorMzy on 2011-05-06
Reinstalling grub won't help; by the time that this error is encountered, the bootloader has already done it's job and you're into the initrd. As you've deduced from the "not clean" message, the filesystem is at least partially damaged (probably due to an unclean shutdown). fsck'ing the partition should fix it, but you can't run fsck on a mounted partition. Make sure that the partition is unmounted, and that you don't have partition editing software open (e.g. parted or gparted). Also, since your partition is sda5, and therefore in an extended partition*, make sure that your swap partition is unmounted too. (Unless the swap partition isn't in the extended partition, in which case it shouldn't matter)

```
sudo swapoff
```

Hopefully this should get you past the "Filesystem mounted or opened exclusively" error.

[SIZE="1"]*Assuming you're using MBR as the partition table, and not GPT or something else.[/SIZE]

---

### Post by candtalan on 2011-05-06
Progress - good!
Although the live CD of 10.04.2 gave the problem mentioned above - (the partition sda5 could not be mounted) I had more success when I ran the ubuntu 10.10 (on /dev/sda8)  which resides on the same hard drive.

I used gparted (version 0.6.2) as it came in ubuntu 10.10 and unlike previously it did not refuse to 'check' sda5. I ran the check and it found inode errors.

The gparted log file is here:

```

&#65279;GParted 0.6.2
Libparted 2.3
Check and repair file system (ext4) on /dev/sda5**00:00:18****( SUCCESS ) 
****
calibrate /dev/sda5**00:00:00****( SUCCESS ) 
****
path: /dev/sda5
start: 102977536
end: 343598219
size: 240620684 (114.74 GiB) 


check file system on /dev/sda5 for errors and (if possible) fix them**00:00:18****( SUCCESS ) 
****
e2fsck -f -y -v /dev/sda5 
****
/dev/sda5: recovering journal
Clearing orphaned inode 136565 (uid=1000, gid=1000, mode=0100644, size=32768)
Clearing orphaned inode 135098 (uid=1000, gid=1000, mode=0100600, size=22052)
Clearing orphaned inode 131519 (uid=1000, gid=1000, mode=0100644, size=2441850)
Clearing orphaned inode 396000 (uid=1000, gid=1000, mode=040700, size=4096)
Clearing orphaned inode 396001 (uid=1000, gid=1000, mode=040700, size=4096)
Clearing orphaned inode 396668 (uid=1000, gid=1000, mode=040755, size=4096)
Clearing orphaned inode 396672 (uid=1000, gid=1000, mode=0100600, size=1977318)
Clearing orphaned inode 396670 (uid=1000, gid=1000, mode=0100600, size=763098)
Clearing orphaned inode 396669 (uid=1000, gid=1000, mode=0100600, size=276)
Clearing orphaned inode 396671 (uid=1000, gid=1000, mode=0100600, size=761263)
Clearing orphaned inode 396665 (uid=1000, gid=1000, mode=040700, size=4096)
Clearing orphaned inode 396667 (uid=1000, gid=1000, mode=040700, size=4096)
Clearing orphaned inode 395799 (uid=1000, gid=1000, mode=040755, size=36864)
Clearing orphaned inode 395870 (uid=1000, gid=1000, mode=0100600, size=16057312)
Clearing orphaned inode 395863 (uid=1000, gid=1000, mode=0100600, size=6698671)
Clearing orphaned inode 395801 (uid=1000, gid=1000, mode=0100600, size=131348)
Clearing orphaned inode 395867 (uid=1000, gid=1000, mode=0100600, size=7651063)
Clearing orphaned inode 139553 (uid=1000, gid=1000, mode=0100644, size=3519779)
Clearing orphaned inode 137698 (uid=1000, gid=1000, mode=0100644, size=32768)
Clearing orphaned inode 136900 (uid=1000, gid=1000, mode=0100600, size=16164)
Clearing orphaned inode 143377 (uid=1000, gid=1000, mode=0100644, size=32768)
Clearing orphaned inode 132881 (uid=1000, gid=1000, mode=0100600, size=16168)
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information

/dev/sda5: ***** FILE SYSTEM WAS MODIFIED *****

395241 inodes used (5.26%)
1187 non-contiguous files (0.3%)
490 non-contiguous directories (0.1%)
# of inodes with ind/dind/tind blocks: 0/0/0
Extent depth histogram: 361353/284
20058258 blocks used (66.69%)
0 bad blocks
3 large files

300035 regular files
52223 directories
60 character device files
26 block device files
0 fifos
929 links
42837 symbolic links (33457 fast symbolic links)
51 sockets
--------
396161 files
e2fsck 1.41.12 (17-May-2010)


grow file system to fill the partition**00:00:00****( SUCCESS ) 
****
resize2fs /dev/sda5 
****
resize2fs 1.41.12 (17-May-2010)
The filesystem is already 30077585 blocks long. Nothing to do!

```
So far so good.
But the question which remains fo rme is - what on earth would have caused such a problem?
Is my hardware somehow failing?
Is there some peculiar bug?

Comments appreciated, and thanks for reading.
My fingers remain crossed for best luck.

---

### Post by candtalan on 2011-05-06
> **WorMzy said:**
> Reinstalling grub won't help; by the time that this error is encountered, the bootloader has already done it's job and you're into the initrd. As you've deduced from the "not clean" message, the filesystem is at least partially damaged (probably due to an unclean shutdown). fsck'ing the partition should fix it, but you can't run fsck on a mounted partition. Make sure that the partition is unmounted, and that you don't have partition editing software open (e.g. parted or gparted). Also, since your partition is sda5, and therefore in an extended partition, make sure that your swap partition is unmounted too. (Unless the swap partition isn't in the extended partition, in which case it shouldn't matter)

```
sudo swapoff
```

Hopefully this should get you past the "Filesystem mounted or opened exclusively" error.

Ah! yes, thanks, I did not recognise the extended partition and swap, so that was probaly it!

Anyway as you can see, I did get to do a check, more by luck than judgement :-)

An unclean shutdown? I was not really aware of this but it could be, thanks.

---

### Post by WorMzy on 2011-05-06
> **candtalan said:**
> An unclean shutdown? I was not really aware of this but it could be, thanks.

Did you experience a power-outage or something similar just before you encountered this problem? Or did you do a "hard reboot" (press and hold the power button for three seconds)? These are the two most common causes of this problem (AFAIK).

Anyway, I trust everything is working again now?

---

