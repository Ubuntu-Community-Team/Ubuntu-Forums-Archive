---
title: "NTFS compatibility on LInux?"
date: 2010-09-06
forum: General Help
---

### Post by arcelivez on 2010-09-06
Hello,

well, I've moved to Linux half a year ago. And I still have some mess with half of my drives since reordering everything requires time and fast temporary storage, which caused me the problems. So I have two windows partitions (NTFS). And I'm thinking of formatting one which has Windows Vista, the other partition has Windows 7 on it, so I want the Windows Vista partition (1/3 of my hdd size) to be perfectly accessible from both - Linux and Windows, even though I do use Linux more. The Windows 7 drive is for me too small.

So what I'm asking is what's the best solution for both os'es using the same drive? Will NTFS work fine? I don't want to divide that partition since small partitions generally are annoying and I already have many of them...

I personally haven't noticed any problems in Ubuntu with that NTFS partition, but gotta admit that I haven't used it much either, since it was full, so I don't really know about what problems could that lead to?

Thanks in advance.

---

### Post by VCoolio on 2010-09-06
considering you want access to it from both windows and linux, ntfs is the way to go. Linux support is ok, but sometimes there are annoyances (like cpu usage while writing to it; don't use it as target partition for torrent downloads for example). Were it linux-only, go ext3/4 or something fancy like jfs or xfs.

---

### Post by Julita on 2010-09-06
I wouldn't suggest using EXT4 since it's pretty much unstable. I used reiserfs, I prefer it, but, surely, ext 3 would do nicely since you can access it from Win using a very comprehensive guide of a free programme that enables to access ext3/ext2 drive from Win. NTFS support is now enabled by default, so you don't have to install additional programmes. I however, sometimes use gigolo. It is the tool to manage your disk partitions, shared or not.

---

### Post by WorMzy on 2010-09-06
When it comes to file systems, I'd much rather trust Linux with an NTFS partition, than trust Windows with a EXT2/3 partition.

I have a terabyte drive, formatted as NTFS, which I use as storage space for all my OS'. Haven't encountered any problems yet.

---

### Post by arcelivez on 2010-09-06
Hmm, the idea of making it ext3 sounds not bad, but I guess since my documents are going to be there it might not work so well in windows? I mean i've heard that ext2 (not sure whether ext3 is supported in win?) was only accessible in windows like accessing an archive? Or will it be shown there as a normal drive and will my documents work fine?

---

### Post by Julita on 2010-09-06
Everything will work fine; ext3 is the best option both for Linux and Win; you can google how to read/write into partition ext3 from Win, I use it myself! It works like a charm; the programme assigns a particular letter to Linux partition, and you can access it with read/write permissions from My Computer just as C:! I do not have my netbook with me now, but I found it through google!

---

### Post by arcelivez on 2010-09-06
Hmm, thanks, I might give it a try. :)

---

### Post by arcelivez on 2010-09-06
Maybe I could also ask now about the partitions:

The partition which was previously NTFS is now formatted as ext3, however in Disk Utility I see, that the partition type is HPFS/NTFS (0x07). Is it normal? This partition type is also on the other windows NTFS partition, all the partitions that have been made by linux have the type: Linux (0x*). Is this important and does this effect anything in any way?

---

### Post by printfw on 2010-09-06
> **arcelivez said:**
> The partition which was previously NTFS is now formatted as ext3, however in Disk Utility I see, that the partition type is HPFS/NTFS (0x07). Is it normal? This partition type is also on the other windows NTFS partition, all the partitions that have been made by linux have the type: Linux (0x*). Is this important and does this effect anything in any way?
It's not normal. If partition formatted as ext3, its type is Linux.

---

### Post by arcelivez on 2010-09-06
> **printfw said:**
> It's not normal. If partition formatted as ext3, its type is Linux.

I guess you were right, somethings not right. I can't mount in on Linux, because I think it tries to mount it as NTFS. It's the primary partition in my partition table and since Windows partitioned it it's meant to be NTFS only I guess?? 

I'm affraid, that to be able to reformat it to ext3 correctly, I would have to delete that partition, but since it's the primary partition I can't do that, because I will loose the partitions and data on the Extended partition? Right?

---

### Post by asmoore82 on 2010-09-06
> **Julita said:**
> I wouldn't suggest using EXT4 since it's pretty much unstable. I used reiserfs, I prefer it, but, surely, ext 3 would do nicely since you can access it from Win using a very comprehensive guide of a free programme that enables to access ext3/ext2 drive from Win. NTFS support is now enabled by default, so you don't have to install additional programmes. I however, sometimes use gigolo. It is the tool to manage your disk partitions, shared or not.

I've been using ext4 heavily for a while now with no issues whatsoever.

I have, however, seen an ext bork'd by the windows "compatibility."

Use NTFS when compatibility is necessary - just remember that it
cannot store proper ownership and permissions.

---

### Post by oldfred on 2010-09-06
If you installed 7 after Vista your 7 boot files are probably inside the Vista partition and you will not be able to boot 7 without repairs of the boot.

Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

I do not like to use any other operating system to write into another system partition. I much prefer separate data partitions and small system partitions.

Mount, hide & link windows partition
[http://ubuntuforums.org/showthread.php?t=1397508](http://ubuntuforums.org/showthread.php?t=1397508)
Share Windows partition:
[http://lifehacker.com/348858/use-a-single-data-store-when-dual-booting](http://lifehacker.com/348858/use-a-single-data-store-when-dual-booting)

---

### Post by printfw on 2010-09-07
So as you said, you already formatted a partition as ext3. What tool did you use? And please, give an output of *sudo fdisk -l*

---

### Post by Dayofswords on 2010-09-07
> **VCoolio said:**
> don't use it as target partition for torrent downloads for example

i learned the hard way, man it was fragmented like crazy

---

### Post by arcelivez on 2010-09-07
> **oldfred said:**
> If you installed 7 after Vista your 7 boot files are probably inside the Vista partition and you will not be able to boot 7 without repairs of the boot.

Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

I do not like to use any other operating system to write into another system partition. I much prefer separate data partitions and small system partitions.

Mount, hide & link windows partition
[http://ubuntuforums.org/showthread.php?t=1397508](http://ubuntuforums.org/showthread.php?t=1397508)
Share Windows partition:
[http://lifehacker.com/348858/use-a-single-data-store-when-dual-booting](http://lifehacker.com/348858/use-a-single-data-store-when-dual-booting)

Yeah, that's exactly the case with boot problems.
The only difference is that I had a funny thing happen to me: Windows 7 was installed after the Windows Vista installation became corrupt (blue screen at boot) and nothing seemed to help it. and then after 9 months, something happened and windows 7 wouldn't boot up in absolutely the same way as Win Vista previously. The funny thing about that is that Windows Vista now worked fine again instead. However it was very outdated to me (obviously like waking up George Washington from dead) and I decided to delete it, with future hopes to get the win 7 installation running. 

Thanks for the links btw, they're really useful. :)

---

### Post by arcelivez on 2010-09-07
> **printfw said:**
> So as you said, you already formatted a partition as ext3. What tool did you use? And please, give an output of *sudo fdisk -l*

Here's the output:
```

arturas@Universe:~$ sudo fdisk -l
[sudo] password for arturas: 

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x77063262

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1306    10485760   27  Unknown
/dev/sda2   *        1306       14008   102025212    7  HPFS/NTFS
/dev/sda3           14008       31082   137148417    f  W95 Ext'd (LBA)
/dev/sda4           31083       38913    62902507+  83  Linux
/dev/sda5           14008       20116    49062912    7  HPFS/NTFS
/dev/sda6           20116       25222    41014272   83  Linux
/dev/sda7           25222       25611     3124224   82  Linux swap / Solaris
/dev/sda8           25611       31082    43943936   83  Linux

```

As you can see, the /dev/sda2 shows the System HPFS/NTFS even though it's formatted as ext3.

I formatted it using the "Disk Utility" in Ubuntu. It didn't let me at first, but after a few restarts it formatted it. It also didn't want to mount the drive, because I think it was trying to mount it as ntfs and I had formatted it as ext3, but I mounted it in fstab just like the windows drive, but changed it's type to ext3 instead of ntfs and it seems to work great right now.

Now I'll just see if I can recover my Win 7 installation to work again and make a different partition have the bootable flag.

---

### Post by arcelivez on 2010-09-07
OK, now it's ****ed up.

I backed up my win7 Partition to the newly formatted ext3 partition.

I formatted win7 partition and installed a fresh copy of windows on it.

And there we go, the ext3 partition has been secretly reformatted back to NTFS by Windows. All the data lost (so both, the real data and the backup got lost). And the secretly formatted drive can now be mounted on Ubuntu as NTFS, but is not even visible in Windows, it is just used for Windows boot manager -_-.

So I warn everyone not to format windows created partitions with linux filesystems, cause windows might wipe it out and your data is gone forever!!! :/

---

### Post by bodhi.zazen on 2010-09-07
> **Julita said:**
> I wouldn't suggest using EXT4 since it's pretty much unstable. 

I would disagree with that statement, ext4 is stable, has been for some time now. In fact, EXT4 is the default file system for many OS including Ubuntu and Fedora.

---

### Post by bodhi.zazen on 2010-09-07
> **arcelivez said:**
> So I warn everyone not to format windows created partitions with linux filesystems, cause windows might wipe it out and your data is gone forever!!! :/

Windows can be a pain that way, but so can Ubuntu (any Linux distro really) and the various BSD's.

You need to be very cautious with installing an OS and take great care to understand what, if any, partitions are going to be re-formatted.

---

### Post by arcelivez on 2010-09-07
> **bodhi.zazen said:**
> Windows can be a pain that way, but so can Ubuntu (any Linux distro really) and the various BSD's.

You need to be very cautious with installing an OS and take great care to understand what, if any, partitions are going to be re-formatted.

True. It's not the first time I see that an OS causes problems for another OS... 

And about my situation: of course, would I have the money, I would buy an external USB drive and back everything up and then partition everything the way I would like to, make everything work and then transfer the old data back. Unfortunately I am not capable to do that in this case... :)

---

