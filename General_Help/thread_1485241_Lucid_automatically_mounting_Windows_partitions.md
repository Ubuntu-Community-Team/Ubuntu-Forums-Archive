---
title: "Lucid automatically mounting Windows partitions"
date: 2010-05-16
forum: General Help
---

### Post by mchamartin on 2010-05-16
Fairly new to Ubuntu (started with Karmic), now dualbooting Lucid and Windows 7.  Lucid is automatically mounting my NTSC partitions, which is pretty convenient since I store all my media there, but I recently deleted one of the partitions and just extended the other one.  Now Lucid is still trying to automatically mount the partition that no longer exists and giving me an error message every time I boot up.  Not really a big deal, just a minor annoyance, but I'm wondering what I do to make it realize the partition is gone.

---

### Post by michy99 on 2010-05-16
Run these commands in a terminal and post the output here.```
sudo fdisk -l
cat /etc/fstab
```

---

### Post by mchamartin on 2010-05-16
sudo fdisk -l
> Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x56cc1c6c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              13       56624   454725632    7  HPFS/NTFS
/dev/sda3           56624       58741    16999425    5  Extended
/dev/sda5           56624       57122     3999744   82  Linux swap / Solaris
/dev/sda6           57122       58741    12998656   83  Linux

cat /etc/fstab
> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc	/proc	proc	nodev,noexec,nosuid	0	0
#Entry for /dev/sda6 :
UUID=14b380ce-c52a-429b-8410-57e14df54aca	/	ext4	errors=remount-ro	0	1
#Entry for /dev/sda1 :
UUID=269C6C5E9C6C2A8F	/media/System_Reserved	ntfs	defaults,nls=utf8,umask=0222	0	0
#Entry for /dev/sda2 :
UUID=E2CA7B93CA7B6329	/media/sda2	ntfs-3g	defaults,locale=en_US.utf8	00
UUID=0CE887B5E8879C18	/media/0CE887B5E8879C18	ntfs-3g	defaults,nosuid,nodev,locale=en_US.utf8	0	0
#Entry for /dev/sda5 :
UUID=49133920-de8f-4a66-a6c6-a27461525efd	none	swap	sw	0	0

Basically there's a main Windows partition, there's a System Reserved partition Windows created, there's the main Ubuntu partition, swap space, and another bit of open space that I left because I'm thinking of installing OS X (as more of a novelty than anything else, I guess).  There was also formerly a larger NTSC partition that I used just for general storage, but my Windows partition was getting really tight and obviously Ubuntu can get at the media whether it's in a dedicated storage partition or just in the Windows boot partition, so I just deleted it and extended the other one.

---

### Post by michy99 on 2010-05-16
I think I see the problem, but just to be sure, what is the output of```
sudo blkid
```

---

### Post by garvinrick4 on 2010-05-16
Michy99 is working on your problem. But I will make a couple of suggestions to make a partition
in gparted when you make the room out of sda2 and just name it "data" or something and format it fat32 that way windows will make it a F drive or whatever letter is open and it will show up in Places drop down as "data" and you will have a partition they both can use since fat32 is OK with Windows and Linux. Is good to defrag Windows about 2 times before you shrink the partition. Always put boot in sda in advanced tab on last page in gparted when installing an OS.
If you have 2 or more gig of Ram I do not think you will use swap unless you do desktop publishing or something. It is hard for me to use over 1 gig in Linux. There are 2 UUID #'s in sda2 also. One you do not want hanging around. You have deleted your Recovery partition sda4 so you have 1 Primary partition left to use, which is nice. Make sure you keep your Windows disks in safe place. If you install OS X make the partition sda4 and Primary in other words. Know how to reinstall grub2 in Live CD before you install another OS that does not use GRUB2, might overwrite your GRUB.

Everytime you mess with your sda do not forget to:

```
sudo update-grub
```

---

### Post by mchamartin on 2010-05-16
sudo blkid
> /dev/sda1: LABEL="System Reserved" UUID="269C6C5E9C6C2A8F" TYPE="ntfs" 
/dev/sda2: UUID="E2CA7B93CA7B6329" TYPE="ntfs" 
/dev/sda5: UUID="49133920-de8f-4a66-a6c6-a27461525efd" TYPE="swap" 
/dev/sda6: UUID="14b380ce-c52a-429b-8410-57e14df54aca" TYPE="ext4" 

> Michy99 is working on your problem. But I will make a couple of suggestions to make a partition
in gparted when you make the room out of sda2 and just name it "data" or something and format it fat32 that way windows will make it a F drive or whatever letter is open and it will show up in Places drop down as "data" and you will have a partition they both can use since fat32 is OK with Windows and Linux. Is good to defrag Windows about 2 times before you shrink the partition. Always put boot in sda in advanced tab on last page in gparted when installing an OS.
If you have 2 or more gig of Ram I do not think you will use swap unless you do desktop publishing or something. It is hard for me to use over 1 gig in Linux. There are 2 UUID #'s in sda2 also. One you do not want hanging around. You have deleted your Recovery partition sda4 so you have 1 Primary partition left to use, which is nice. Make sure you keep your Windows disks in safe place. If you install OS X make the partition sda4 and Primary in other words. Know how to reinstall grub2 in Live CD before you install another OS that does not use GRUB2, might overwrite your GRUB.
I did all the partitioning in Windows disk management just because that's what I've always used before switching to Linux and what I'm more comfortable with.  There was never actually a recovery partition, I bought and installed this drive myself a few months ago for a three year old laptop.  The extra partition was solely for storing music, movies, etc.  But the Windows partition was getting too full and obviously it isn't really necessary for purposes of sharing between Windows and Ubuntu to have a separate NTSC partition, so I canned it.

I agree that the swap probably isn't necessary but on a 500 gig hard drive I decided I could spare a few gigs anyway.  I actually just got a new laptop a few weeks ago and moved the hard drive over with fresh installs of Windows and Ubuntu.  The old laptop actually did need the swap, but this one's got plenty of RAM and probably doesn't.  Nonetheless, I've got an abundance of hard drive space, so whatever -- unless there's some drawback to having too much swap space that I don't know about.

---

### Post by michy99 on 2010-05-16
Just as I suspected, there is an entry in /etc/fstab for the partition which no longer exists. Open for editing:```
gksudo gedit /etc/fstab
```Remove this line and save the file:```
UUID=0CE887B5E8879C18 /media/0CE887B5E8879C18 ntfs-3g defaults,nosuid,nodev,locale=en_US.utf8 0 0
```That should take care of it. You can test with```
sudo mount -a
```and see if you get any errors.

---

### Post by mchamartin on 2010-05-16
Worked perfectly, thanks for all the help.

---

