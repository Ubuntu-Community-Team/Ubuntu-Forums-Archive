---
title: "partition dissapeared"
date: 2010-12-02
forum: General Help
---

### Post by metacortex88 on 2010-12-02
Hey guys, 

I booted my laptop up this morning to find that Ubuntu 10.10 will no longer boot. Here is some background.

I have a Raid 0 setup with sda and sdb. For the last day or two upon boot, it was asking me to run some file system checks (hind sight I should have just sucked it up and wait for it) but I canceled out of them as I have been extremely busy. Also, I upgraded my kernel to the latest available from the repos. I am not sure if the kernel upgrade has anything to do with it or just coincidence. 

I have booted up with a live distro on a USB stick and here is what I am seeing


```

root@bt:/dev# ls -alh sd*
brw-rw---- 1 root disk 9, 127 Dec  2 10:44 sda
brw-rw---- 1 root disk 9, 126 Dec  2 10:44 sda1
brw-rw---- 1 root disk 8,  16 Dec  2 10:41 sdb
brw-rw---- 1 root disk 8,  32 Dec  2 10:41 sdc
brw-rw---- 1 root disk 8,  33 Dec  2 10:41 sdc1
brw-rw---- 1 root disk 8,  34 Dec  2 11:06 sdc2
brw-rw---- 1 root disk 8,  37 Dec  2 10:41 sdc5
root@bt:/dev# fdisk -l

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sdb doesn't contain a valid partition table

Disk /dev/sdc: 16.1 GB, 16125001728 bytes
255 heads, 63 sectors/track, 1960 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00004790

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1        1872    15036808+  83  Linux
/dev/sdc2            1873        1960      706860    5  Extended
/dev/sdc5            1873        1960      706828+  82  Linux swap / Solaris

```

So I am able to see sda in /dev but fdisk does not see it. When looking at gparted, it only is able to look at sdb and sdc (my usb stick). The weird thing is that I also have Windows 7 installed on this raid and it is able to boot without any issues so I know the entire sda hasn't died on me. 

I am trying to figure out why I am seeing this behavior and hopefully fix it without data loss. Any help is appreciated. 

Thanks!

---

### Post by ronparent on 2010-12-02
There currently is a bug with gparted that prevents it from seeing a raid array. Simply install kpartx. Just be aware that the kpartx install to a live session is non persistent and will last only for the live session. But it will permit you to see your raid partitions so you can see if your raids are still intact.

---

### Post by metacortex88 on 2010-12-03
Here is what I am seeing with kpartx

```

root@bt:~# kpartx -l /dev/sda
gpt: 0 slices
llseek error
dos: 4 slices
sda1 : 0 755146689 /dev/sda 63
sda2 : 0 204800 /dev/sda 755146752
sda3 : 0 209510400 /dev/sda 755351552
sda4 : 0 11904165 /dev/sda 964863900
root@bt:~# kpartx -l /dev/sdb
gpt: 0 slices

```

So, it looks like the partitions on sdb died (as opposed to sda as I originally thought). After playing with kpartx for a bit, gparted is now able to see both sda and sdb but showing them as unallocated as I would probably expect due to the raid 0. 

Any other ideas?

---

### Post by ronparent on 2010-12-03
What do you get when you run gparted with kpartx installed to the live cd session? Gparted should show the raid partitions in addition to the unalocated sda and sdb if the raid partition table is not damaged.

---

### Post by metacortex88 on 2010-12-03
The only drives I see are sda, sdb, and sdc. sda and sdb are fully unallocated. If I understand correctly, I should also see a logical drive in there as well? Generally when I have had to mount it from a live distro in the past I would have to mount the drive that was in /dev/mapper but I only see the control.

---

### Post by srs5694 on 2010-12-03
> **metacortex88 said:**
> Here is what I am seeing with kpartx

```

root@bt:~# kpartx -l /dev/sda
gpt: 0 slices
llseek error

```I'm not all that familiar with kpartx, but when I tried it on an MBR disk, it didn't mention anything about GPT (which is an alternative to the more common MBR partitioning), so I'm wondering if you might have some leftover GPT data on your disks that's causing you problems. I recommend you download and install the latest version of [GPT fdisk,]("http://sourceforge.net/projects/gptfdisk/files/") type "sudo gdisk -l /dev/sda" and "sudo gdisk -l /dev/sdb", and post the results here.

---

### Post by metacortex88 on 2010-12-03
```

root@bt:~# gdisk -l /dev/sda
GPT fdisk (gdisk) version 0.6.13

Unable to seek to 964863900! Aborting!
MBR signature in logical partition invalid; read 0x0220, but should be 0xAA55
Partition table scan:
  MBR: MBR only
  BSD: not present
  APM: not present
  GPT: not present


***************************************************************
Found invalid GPT and valid MBR; converting MBR to GPT format.
***************************************************************


Warning! Secondary partition table overlaps the last partition by
476464817 blocks!
You will need to delete this partition or resize it in another utility.
Disk /dev/sda: 488397168 sectors, 232.9 GiB
Logical sector size: 512 bytes
Disk identifier (GUID): D5CC8FD9-FD79-4391-A791-E03CCF41E7D9
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 488397134
Partitions will be aligned on 1-sector boundaries
Total free space is 29 sectors (14.5 KiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1              63       755146751   360.1 GiB   0700  Linux/Windows data
   2       755146752       755351551   100.0 MiB   0700  Linux/Windows data
   3       755351552       964861951   99.9 GiB    0700  Linux/Windows data
root@bt:~# gdisk -l /dev/sdb
GPT fdisk (gdisk) version 0.6.13

Partition table scan:
  MBR: not present
  BSD: not present
  APM: not present
  GPT: not present

Creating new GPT entries.
Disk /dev/sdb: 488397168 sectors, 232.9 GiB
Logical sector size: 512 bytes
Disk identifier (GUID): B7A42508-4C48-4584-B1D2-B543354A7AB2
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 488397134
Partitions will be aligned on 2048-sector boundaries
Total free space is 488397101 sectors (232.9 GiB)

Number  Start (sector)    End (sector)  Size       Code  Name

```

---

### Post by ronparent on 2010-12-03
What do you get if you run 'sudo dmraid -s'.

---

### Post by srs5694 on 2010-12-04
There's no hint of GPT data in the gdisk output, so my guess is that something else was triggering the "gpt: 0 slices" lines in the kpartx output.

The gdisk output does incidate, though, that there's a problem with an extended partition on /dev/sda, and gdisk couldn't find any valid partition table on /dev/sdb. Without knowing precisely how the disks were partitioned and assembled into a RAID array initially, I can only speculate wildly about what's going on, but clearly it's a mess. Perhaps you should elaborate about how the RAID array was initially assembled. Did you partition it, link the partitions into RAID devices (/dev/dm0, etc.), and use them directly; partition it, link the partitions into one big /dev/dm0 device, and partition that; or link the *unpartitioned* disks into an array (/dev/dm0) and then partition that (/dev/dm0p1, etc.)?

---

### Post by metacortex88 on 2010-12-06
> **ronparent said:**
> What do you get if you run 'sudo dmraid -s'.

cant get it at the moment but as soon as I am able to I will 

> **srs5694 said:**
>  Did you partition it, link the partitions into RAID devices (/dev/dm0, etc.), and use them directly; partition it, link the partitions into one big /dev/dm0 device, and partition that; or link the *unpartitioned* disks into an array (/dev/dm0) and then partition that (/dev/dm0p1, etc.)?

I didn't do any of that. It is a hardware raid and when installing ubuntu on the unpartitioned drives it only recognized one physical drive to install to and that was the end of that.

---

### Post by srs5694 on 2010-12-06
If it's hardware RAID, I recommend you start dealing with whatever hardware RAID utilities you've got for your controller. It's possible that one of your disks has failed and this is why it's acting weird; or perhaps some sort of setting has gone out of whack.

---

### Post by ronparent on 2010-12-06
I've reviewed the entire post but I can only surmise that your raid system is based on a MB chip set and would be referred to as a fakeraid by the Linux community. If that were the case when you raid was setup in bios meta data would have been written to both component drives of your raid0 set and remains there. A primary function of the dmraid software (run in a terminal) is to discover and report the status of the raid set. Thus to let you know what the health of the raid set is you need to run a command like 'sudo dmraid -s'. So if you have a true fakeraid you would then know where you stand.

Unfortunately since it is a raid0 (stripped raid) the integrity of your data depends on the health of both drives. If one drive fails all data is lost! If you want help with this please let us know where you stand.

---

### Post by metacortex88 on 2010-12-06
> **ronparent said:**
> I've reviewed the entire post but I can only surmise that your raid system is based on a MB chip set and would be referred to as a fakeraid by the Linux community. If that were the case when you raid was setup in bios meta data would have been written to both component drives of your raid0 set and remains there. A primary function of the dmraid software (run in a terminal) is to discover and report the status of the raid set. Thus to let you know what the health of the raid set is you need to run a command like 'sudo dmraid -s'. So if you have a true fakeraid you would then know where you stand.

Unfortunately since it is a raid0 (stripped raid) the integrity of your data depends on the health of both drives. If one drive fails all data is lost! If you want help with this please let us know where you stand.

I am by no means an expert on raids as this is the only system I have ever used with this setup but I am fully aware of the pros and cos of a striped setup without any parity and I know that if one half is lost that is the end of it. I know that a drive did not die because as stated before, I am able to boot a windows 7 install off of the exact same raid. I am just confused as why all the sudden the ubuntu install dies. The raid utility in my bios reports as the raid being healthy and it is confirmed with the dmraid output

```
root@bt:~# dmraid -s
*** Group superset isw_fgeeaddhg
--> Active Subset
name   : isw_fgeeaddhg_Volume0
size   : 976783872
stride : 256
type   : stripe
status : ok
subsets: 0
devs   : 2
spares : 0

```

Wow, here is something odd. After running dmraid, all the sudden I have something in /dev/mapper

```
root@bt:/dev/mapper# ls
control                isw_fgeeaddhg_Volume01  isw_fgeeaddhg_Volume03
isw_fgeeaddhg_Volume0  isw_fgeeaddhg_Volume02  isw_fgeeaddhg_Volume05

```

Now that I actually have something in here, I am able to mount the ubuntu partition. And get to the data. This is odd because it was never available to me for the past few days. I am going to go ahead and fsck it now that I have it available but am at a loss as to why it all the sudden came back.

---

### Post by ronparent on 2010-12-06
One of the main functions of dmraid is to assemble the array and post the symbolic links for the array and all its partitions in /dev/mapper. That is what happened. The question is why is it not happening automatically on boot? Or is it?

---

### Post by srs5694 on 2010-12-07
The first post mentioned a kernel upgrade. I'd wager that's the cause of the problem. When the kernel upgrade occurred, the initial RAM disk (aka initrd or initramfs) was also upgraded. It's this initial RAM disk that must normally activate RAID devices, so if the upgrade didn't include the necessary RAID tools, you'd see the symptoms you've got.

Unfortunately, my knowledge of motherboard software RAID and the necessary Linux support tools is a bit limited, as is my knowledge of how Ubuntu in particular handles these things. Thus, I can't offer much in the way of specific suggestions for how to proceed. I can only offer the general suggestion that you need to look into initial RAM disk generation and Linux motherboard software RAID tools and build a new initial RAM disk that includes the necessary tools and activation scripts.

---

### Post by ronparent on 2010-12-07
In general terms the posting by srs5694 is correct. That would be the primary purpose of dmraid during the boot process. In addition, with 10.10, another set of parallel links are set up (dm-0, dm-1, etc.). That should be evidenced in the boot logs. Doing a search in the logs on 'isw_fgeeaddhg_Volume0' or 'dm-' etc. should reveal what the boot process is doing with these. Unfortunately I am currently booted into Win 7 or I could give you more specific directions. If you are still having problems post again.

---

