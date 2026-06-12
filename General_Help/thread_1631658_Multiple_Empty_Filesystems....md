---
title: "Multiple Empty Filesystems..."
date: 2010-11-26
forum: General Help
---

### Post by ImprisonedPride on 2010-11-26
Hello and thanks in advance for checking out my problem.

I'm using a laptop with a 120GB hdd. I initially wiped the hdd and installed Windows 7 which is the partition at the bottom of the following table (/dev/sda2). 

```
Filesystem            Size  Used Avail Use% Mounted on
/dev/loop0             29G  4.6G   23G  17% /
none                  493M  288K  492M   1% /dev
none                  497M  1.1M  496M   1% /dev/shm
none                  497M   96K  497M   1% /var/run
none                  497M     0  497M   0% /var/lock
none                  497M     0  497M   0% /lib/init/rw
/dev/sda3              83G   31G   53G  37% /host
/dev/sda2              30G  8.6G   21G  30% /media/8866FD9F66FD8DE6

```

I then used Wubi with Ubuntu 10.10 to install to the remainder of the hdd or so I thought (/dev/sda3). I have been using Ubuntu only now for a few weeks since the install and realized my drive-space was getting low (I assumed this was due to a lot of download videos and misc. stuff). I cleared all that out and only gained a few gigs. It was not until I saw a "df -h" report in terminal that I realized what is going on; I'm operating on /dev/loop0, and I cannot seem to utilize the missing 53GB of storage space stuck in /dev/sda3 (I have about 45GB of data to temporarily store on my laptop before moving it somewhere else). Does anyone know what I might have done wrong and *hopefully* how to fix the issue without a reinstall? I need to regain as much storage space as I can (if need be I may be able to completely remove windows 7 for the time being).

Thanks again.

---

### Post by ImprisonedPride on 2010-11-27
Bump/Update...

I just wanted to say that I may have misspoke myself in my original post. If you look at the table the sum of the size column is well above 120GB; the limit of my hdd. I believe this is because the Used 31GB of /dev/sda3 actually IS /dev/loop0. I installed gparted but naturally, it only shows me /dev/sda1, /dev/sda2, and /dev/sda3. The numerous "None" partitions are not there, nor is loop0. My original intention was to simply remove the other partitions to try to extend /dev/loop0 to the hdd's maximum capacity but that is not possible at the moment. (Of course, this is all speculation and I could be very or completely wrong; I'm not an Ubuntu expert.)

Thanks again for help in advance.

---

### Post by ImprisonedPride on 2010-11-28
last bump... :(

---

### Post by mikewhatever on 2010-11-28
Your dh -f output looks normal. Basically, only the last two are partitions, the rest are not. Don't install Ubuntu inside Windows if you want it on a partition.
You should probably read the [FAQ]("http://wubi.sourceforge.net/faq.php").

---

### Post by ImprisonedPride on 2010-11-28
I didn't install it inside windows. It's on it's own partition. Thought I made it clear but let me rephrase it. Basically, when the HDD was blank and I popped in the W7 cd I formatted the entire thing then made a 30GB partition and installed W7 to it. When W7 finished installing, I went to the disk manager and created another partition with all remaining space (80GB). When I ran Wubi, I selected -that- partition to install to. If I boot back into Windows, its' disk manager reflects this, yet in Ubuntu it's telling me the partition I created is significantly less than that. All I'm trying to figure out is how to reclaim that unused data but it's not telling me it's -really- unused. It's saying it's inside another partition that's in use that has no data on it...

Besides, if what you said about the df -h output is correct, then why is my Ubuntu install operating on 1 permanent partition and a temporary one?

---

### Post by coffeecat on 2010-11-28
> **ImprisonedPride said:**
> I didn't install it inside windows. It's on it's own partition.

....


When I ran Wubi

You used Wubi. That means you installed it "inside" Windows. The fact that you created a separate partition is immaterial. My guess is that this partition is a NTFS one - which is a Microsoft filesystem - and appears as Windows D: or E: or whatever from Windows. Your wubi virtual Ubuntu drive (which is just one big file within the Windows NTFS filesystem) is smaller than the partition it is contained within. That's why you can't claim extra space.

A couple of points to consider. If you want Ubuntu on its own partition running natively, you cannot use NTFS and you cannot use the Windows Disk manager to create it. You must use the partitioner from the Ubuntu live CD. 

So that we can see your partition layout properly, post the output of:

```
sudo fdisk -lu
```

---

### Post by ImprisonedPride on 2010-11-28
```

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x18b39c9d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2          206848    61442047    30617600    7  HPFS/NTFS
/dev/sda3        61442048   234438655    86498304    7  HPFS/NTFS


```

---

### Post by coffeecat on 2010-11-28
Your partition layout is as follows:

sda1 - 104MB - NTFS - this will be your Windows 7 boot partition.
sda2 - 31.3 GB - NTFS your Windows C: partition.
sda3 - 88.6GB - also NTFS. This will appear as D: or E: in Windows and this is where your Ubuntu wubi virtual drive will be.

By the way, those figures are in mega/gigabytes - in base 10. Your df -h output gives you GiB (gibibyte = base 2) figures. That's why the figures are slightly different.

Anyway - in Windows, go to Computer and then to D: or E:, whatever designation your 88.6GB partition has, and look in the D:\ubuntu folder (or E:\ubuntu). You'll find a file of about 30-31GB. That's your Ubuntu virtual root filesystem, what is appearing as /dev/loop0.

A couple of comments. If you want a "proper" Ubuntu installation in a conventional dual-boot, you need to install it to a partition formatted with the Linux filesystem ext4. NTFS will not do. It is possible to convert a wubi install to a conventional one, but I believe the method is somewhat complex. You'll also need a separate swap partition, so a fresh install after correct partitioning might be the best way to go.

Also - 30GB for Windows 7 is really a bare minimum. If you are going to repartition you might want to think about giving it a bit more breathing room.

You might want to read this, together with all the links, before deciding what to do:

[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

**EDIT:** alternatively, since you have so much spare space on the 88.6GB partition and a working wubi install, you might be able to increase the size of the wubi virtual filesystem. I believe this is possible, but I don't know the method. If I find something I'll post back.

---

### Post by ImprisonedPride on 2010-11-28
Thanks for your help coffeecat. The reason there is only 30GB designated for Windows 7 is because I was never intent on keeping Windows 7. However, since no amount of trying would produce a working 10.04 or 10.10 bootable live cd, I had to install Windows 7 as a jumping-off point in which to install Ubuntu from (hence the partitioning). I originally assumed I'd just jump over to Ubuntu and once versed on how to use it, remove the Windows 7 partition and reclaim the space.

I appreciate your help. It's unfortunate that I can't seem to get a working copy of the live cd for 10.04 or 10.10 (being touch and go... sometimes the cd boots fine on other pc's and sometimes it doesn't, but it has -never- worked with my laptop; same goes for bootable usb's). I suppose I will waste -another- day completely backing up my work files in Ubuntu and making -another- fresh install, unless you happen to stumble across a way to make it work.

Thanks again.

---

### Post by dino99 on 2010-11-28
[http://ubuntuforums.org/showpost.php?p=10161428&postcount=2](http://ubuntuforums.org/showpost.php?p=10161428&postcount=2)

---

### Post by ImprisonedPride on 2010-11-28
Thanks for the link. I'm guessing that would probably work for me. However, I don't suppose you can go into a little more detail? I mean, I'm not simply extending this install, I'm creating a new one, right? Also, I've not really worked with gparted or partedmagic. So any extra steps or tuts you can provide would be appreciated.

---

### Post by mikewhatever on 2010-11-28
That should be simple:

1. Make unallocated space, Gparted, Windows, it doesn't matter what you use.
2. Start installing. At the partitioning stage, select the 'Use the largest continuous space' option.
3. Remove the wubi install before or after, since you probably won't need it.

---

### Post by ImprisonedPride on 2010-11-28
You mean after I make the allocated space, I should install from Ubuntu with a copy of the distro I need? If I install from Windows with Wubi I have the feeling I'll be putting myself right back in the place I am now. Thanks.

EDIT: Because basically I can't install from the boot on this laptop.

---

### Post by mikewhatever on 2010-11-28
I meant **un**allocated space (basically unformatted) and installing Ubuntu by booting from the installation cd.
Wubi will always install Ubuntu inside the Windows file system.

---

### Post by ImprisonedPride on 2010-11-28
Well that's no good either way since I can't get a bootable cd to work with this laptop... oh well thanks for the help.

---

