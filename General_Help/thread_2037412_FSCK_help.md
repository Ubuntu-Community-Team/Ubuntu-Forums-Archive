---
title: "FSCK help"
date: 2012-08-04
forum: General Help
---

### Post by cajunlibra on 2012-08-04
I've been having issues over almost 2 years now. It started after an upgrade to 10.10. I had later did a fresh install but it didn't fix my problems.  Most often, my system crashes while using a Flash heavy site(FB games like Cityville or Millionaire City) and even playing online videos from really any site. THe system may slow quite a bit and then just crash.  This is also happening in XP as I am dual-booting.  I have tried to run virus scans using Clam and Bitdefender but they eventually crash as well. Over the past couple of months, I can't even leave Ubuntu running without it getting so bogged down. Yesterday after I got home from work, about 6:30 or so, the clock was still showing 9:40am.

Can someone help me out with what I should do?  I have noticed that my SWAP partition seems to have disappeared. I couldn't tell when that first occured as I have only noticed it a few days ago. I don't remember what commands I ran as I cannot re-find the forums post I was using as a guide. I remember the partition that is designated as the swap just reported 0 when listed. I remember seeing something about a bad or corrupted superblock as well. I'm choosing the forum option over the IRC channel so that I can come back once i have to do any rebooting.

I'm on a LiveCD of 12.04 at the moment and was when I try that last set of repairs.


```
ubuntu@ubuntu:~$ sudo fdisk -l 

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x41ab2316

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *      128520    82043954    40957717+   7  HPFS/NTFS/exFAT
/dev/sda2        82044926   156299263    37127169    5  Extended
/dev/sda5        82044928    83996671      975872   82  Linux swap / Solaris
/dev/sda6        83998720   103567359     9784320    b  W95 FAT32
/dev/sda7       103569408   156299263    26364928   83  Linux

```

---

### Post by CharlesA on 2012-08-04
If you are having problems independent of OS, it sounds like more of a hardware problem tbh.

Have you checks dmesg or syslog on Ubuntu when it starts running slow?

---

### Post by cajunlibra on 2012-08-04
No I haven't. The crash tends to happen quickly and it starts running slowly rather quickly moreso than a gradual slowdown.

Which commands should I use to run fsck on my system that would give me the superblock error again? I have NTFS and ext filesystems on the same HDD. I'd like to know for sure if it is just a hardware issue so I can figure that out. I'm not a noob but I am far from an advanced user.

---

### Post by CharlesA on 2012-08-04
You can only run fsck on a Linux file systems, which would be /dev/sda5 and /dev/sda7

If you are on a livecd now, run this from a terminal:

```
sudo fsck -fC /dev/sda5
```
```
sudo fsck -fC /dev/sda7
```

To check the NTFS partitions, you would need to boot Windows.

---

### Post by ajgreeny on 2012-08-04
> **CharlesA said:**
> You can only run fsck on a Linux file systems, which would be /dev/sda5 and /dev/sda7

If you are on a livecd now, run this from a terminal:

```
sudo fsck -fC /dev/sda5
``````
sudo fsck -fC /dev/sda7
```To check the NTFS partitions, you would need to boot Windows.
Unless I am mistaken I don't think you can run fsck on a swap partition, so you may get an error when trying it on sda5.

Why do you think you have no swap partition; there is one showing at sda5, so lets see the output of ```
sudo blkid
cat /etc/fstab
free -m
```to see if and why it is not being mounted at boot.

---

### Post by CharlesA on 2012-08-04
> **ajgreeny said:**
> Unless I am mistaken I don't think you can run fsck on a swap partition, so you may get an error when trying it on sda5.

You are probably right. I don't think I've ever actually done an fsck on it, cuz it is just temp storage.

---

### Post by cajunlibra on 2012-08-04
It's not that I don't have one. I ran a command previously and the results showed a 0 for it. Maybe this was for its size?  I can't remember what command I ran. I did look similar to this. Is it a 0 because I'm on the LiveCD?

```
ubuntu@ubuntu:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          1001        737        263          0         41        202
-/+ buffers/cache:        493        507
Swap:            0          0          0

```

Do any of you hae experience with ntfsck? I've seen it as an option for ntfs partitions.

```
ubuntu@ubuntu:~$ sudo fsck -fC /dev/sda5
fsck from util-linux 2.20.1
e2fsck 1.42 (29-Nov-2011)
fsck.ext2: Superblock invalid, trying backup blocks...
fsck.ext2: Bad magic number in super-block while trying to open /dev/sda5

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

```

```
ubuntu@ubuntu:~$ sudo fsck -fC /dev/sda7
fsck from util-linux 2.20.1
e2fsck 1.42 (29-Nov-2011)
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure                                           
Pass 3: Checking directory connectivity                                        
Pass 4: Checking reference counts                                              
Pass 5: Checking group summary information                                     
/dev/sda7: 522448/1648320 files (0.9% non-contiguous), 4940717/6591232 blocks  

```

```
ubuntu@ubuntu:~$ sudo blkid
/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="AC80DF9980DF687A" TYPE="ntfs" 
/dev/sda6: UUID="905B-B3C7" TYPE="vfat" 
/dev/sda7: UUID="af52bf7f-eb58-45ed-bf2d-d57f547d9351" TYPE="ext4" 
/dev/sr0: LABEL="Ubuntu 12.04 LTS i386" TYPE="iso9660" 

```

```
ubuntu@ubuntu:~$ cat /etc/fstab
overlayfs / overlayfs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0

```

What next?  Thank you all for your help.

---

### Post by cajunlibra on 2012-08-04
I guess it was 0 cuz I was on the LiveCD. Here is the output of free -m while logged into Ubuntu.

```
            total       used       free     shared    buffers     cached
Mem:          1001        918         82          0         22        213
-/+ buffers/cache:        682        318
Swap:          952         19        933

```

---

### Post by oldfred on 2012-08-04
Linux fsck is for the ext2, ext3 & ext4 family of formats. You cannot use it on Windows formats like NTFS or FAT. Use chkdsk from Windows for those formats. 

You actually do not want to use swap as it is 10 times or more slower than RAM. Hard drive speed vs. RAM. But if you do not have a lot of RAM you may need swap when you run out of RAM. So actually having free show 0 as use is good. But if you load a lot of larger applications with 1GB of RAM then you may start using swap, but also may notice it is slower responding.

---

### Post by cajunlibra on 2012-08-04
> **oldfred said:**
> Linux fsck is for the ext2, ext3 & ext4 family of formats. You cannot use it on Windows formats like NTFS or FAT. Use chkdsk from Windows for those formats. 

You actually do not want to use swap as it is 10 times or more slower than RAM. Hard drive speed vs. RAM. But if you do not have a lot of RAM you may need swap when you run out of RAM. So actually having free show 0 as use is good. But if you load a lot of larger applications with 1GB of RAM then you may start using swap, but also may notice it is slower responding.

What about dosfstools and ntfsck? I've read about both on the web.

[http://blogs.dailynews.com/click/2010/01/need-to-fsck-a-fat-filesystem.html](http://blogs.dailynews.com/click/2010/01/need-to-fsck-a-fat-filesystem.html)

---

### Post by oldfred on 2012-08-04
ntfsprogs has merged wtih ntfs-3g and if you download the old ntfsprogs it uninstalls the ntfs-3g and you cannot access NTFS partitions anymore. (at least in some versions just after the merger).

---

### Post by ajgreeny on 2012-08-04
> **cajunlibra said:**
> I guess it was 0 cuz I was on the LiveCD. Here is the output of free -m while logged into Ubuntu.

```
            total       used       free     shared    buffers     cached
Mem:          1001        918         82          0         22        213
-/+ buffers/cache:        682        318
Swap:          952         19        933

```
Well, you do have a swap partition and it's running OK.

The error message on your fsck of sda5 is because it's a swap partition, and as I thought, fsck does not work on that type of partition.

You are using quite a lot of RAM, however, and I wonder if your system is overheating a bit, causing the crashes, which I think are completely coincidental to any swap situation.

---

