---
title: "Trying to reinstall, stuck on Install Now?"
date: 2011-01-22
forum: General Help
---

### Post by ZeroRider13 on 2011-01-22
Trying to reinstall ubuntu netbook, because my netbook that came ubuntu preloaded one day just wouldn't boot up and is stuck on <initramfs> 

But I'm trying to reinstall a fresh copy because I've had some problems anyway.  However when I try to reinstall, it brings me to the partition screen after my language option and my option to erase the whole partition, and just shows me my 8.1 GB hardrive and has the rotating cursor after I press Install Now and never leaves the screen.  Is there a way I can reinstall my copy from the live cd or anything or is there any other way?  Please help me out as I am all out of options after trying to reinstall from both my Live screen from my USB stick and the boot screen.  Thanks

---

### Post by meson2439 on 2011-01-22
You're probably installing with *.img image files on your pendrive. Install the *.iso instead. The latest ubuntu netbook is in that format.

If you're unwilling to download, well you could rename one of the files (in that pendrive) with a *.lz and change the extension so that it will become a *.gz instead.

Hope it helps.

---

### Post by kansasnoob on 2011-01-22
When you boot the Live USB right after the System/BIOS screen passes you'll see a screen with two small emblems at the bottom. When that appears you have about 3 seconds to press a key (I always use Enter).

Then you'll see the language selection screen followed by a list of options. Choose "Check CD for defects" first. That takes a few minutes to complete. If it says no errors found then next try the option "Try Ubuntu" rather than install and we'll try and troubleshoot from the live desktop.

---

### Post by ZeroRider13 on 2011-01-22
Ok, I just did what you said and heres what happened:

No errors found.

Currently on Live CD again.

Thanks for helping, what should I do now? =]

---

### Post by kansasnoob on 2011-01-22
Sorry to take so long, sadly I may be out off and on all day.

Regardless let's see how Ubuntu is recognizing your hard drive. You might actually look at Gparted and see if any errors are displayed. It's in System > Administration.

Potentially helpful commands:

```
sudo fdisk -l
```

```
sudo parted -l
```

BTW that's a lower case L in both commands.

I suspect a problem regarding the formatting/partitioning of your drive. Since you're wiping it clean anyway you could use Gparted and select Device > Create partition table. Just be darn sure to select the hard drive and NOT your Live USB or some other data card!

---

### Post by Rubi1200 on 2011-01-22
Go to Applications > Accessories > Terminal and post the output of the following command:

```
sudo parted -l
```(Lowercase L not 1)

When posting back highlight the text and click on # from the toolbar to wrap the text, then submit.

EDIT: beaten to it :-)

---

### Post by kansasnoob on 2011-01-22
Just having a "duh" moment here, when you say, "just shows me my 8.1 GB hardrive and has the rotating cursor after I press Install Now and never leaves the screen", you do mean this screen, eh?

[ATTACH]181729[/ATTACH]

I just want to be sure we're thinking the same.

Are you sure your actual hard drive is only 8.1 GB?

I know it could be but I'm just curious.

---

### Post by ZeroRider13 on 2011-01-22
Yes, thats exactly what I've been staring at for the last 4 hours, and yes it's a good netbook, but I opted for the 8gb version because of the price, it's a ssd.  Also, I am now going to do all of those things, ending with the guy who said to create the partition table.

fdisk-l

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 8069 MB, 8069677056 bytes
255 heads, 63 sectors/track, 981 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0001ccbf

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         933     7490560   83  Linux
Partition 1 does not end on cylinder boundary.
/dev/sda2             933         981      387073    5  Extended
Partition 2 does not end on cylinder boundary.
/dev/sda5             933         981      387072   82  Linux swap / Solaris

Disk /dev/sdb: 4016 MB, 4016046080 bytes
90 heads, 25 sectors/track, 3486 cylinders
Units = cylinders of 2250 * 512 = 1152000 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           4        3487     3917824    b  W95 FAT32

Disk /dev/sdc: 2000 MB, 2000682496 bytes
64 heads, 63 sectors/track, 969 cylinders
Units = cylinders of 4032 * 512 = 2064384 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000b0d56

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1         969     1953439+   6  FAT16

parted -l
ubuntu@ubuntu:~$ sudo parted -l
Model: ATA SSDPAMM0008G1 (scsi)
Disk /dev/sda: 8070MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      1049kB  7671MB  7670MB  primary   ext4            boot
 2      7672MB  8069MB  396MB   extended
 5      7672MB  8069MB  396MB   logical   linux-swap(v1)


Model: JetFlash Transcend 4GB (scsi)
Disk /dev/sdb: 4016MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      4194kB  4016MB  4012MB  primary  fat32        boot


Model: SanDisk Cruzer (scsi)
Disk /dev/sdc: 2001MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      66.0kB  2000MB  2000MB  primary  fat32        boot


Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.
Error: /dev/sr0: unrecognised disk label

----

Also, how exactly do I safely use gparted?  I mean, theres a linux swap, and a nother other than the HD, so I was wondering if I was supposed to format all of them, or how, and what to format to, I have a lot of questions haha, sorry.  Thanks again.

---

### Post by kansasnoob on 2011-01-22
> **ZeroRider13 said:**
> Yes, thats exactly what I've been staring at for the last 4 hours, and yes it's a good netbook, but I opted for the 8gb version because of the price, it's a ssd (sdb1).  Also, I am now going to do all of those things, ending with the guy who said to create the partition table.

I was just double-checking to be sure we were on the same page :)

If Gparted shows any errors that may be very helpful. When an operation is complete you can click on "details" to see what was found.

---

### Post by ZeroRider13 on 2011-01-22
Yeah haha, thank you, if it was that simple I'd be pissed at myself.  Also, what exactly do you mean by the results from gparted?

---

### Post by kansasnoob on 2011-01-22
Aha:

> Device Boot Start End Blocks Id System
/dev/sda1 * 1 933 7490560 83 Linux
**[COLOR="Red"]Partition 1 does not end on cylinder boundary.[/COLOR]**
/dev/sda2 933 981 387073 5 Extended
**[COLOR="Red"]Partition 2 does not end on cylinder boundary.[/COLOR]**
/dev/sda5 933 981 387072 82 Linux swap / Solaris

So, go to Gparted, you'll likely have to click on the SWAP partition and select "swapoff", then "Create partition table". I'm guessing that the default will work with your machine.

But, **[COLOR="Red"]before that[/COLOR]**, post the output of:

```
free -m
```

If you have less than 512MB of RAM installation may be more problematic. Like you may have to reboot the Live USB before trying to install and bypassing the live desktop altogether.

---

### Post by kansasnoob on 2011-01-22
> **ZeroRider13 said:**
> Yeah haha, thank you, if it was that simple I'd be pissed at myself.  Also, what exactly do you mean by the results from gparted?

System > Administration > Gparted:

[ATTACH]181732[/ATTACH]

If there are any errors you'll see the ability to view results.

---

### Post by kansasnoob on 2011-01-22
I do hope you're not still using 9.04 as indicated in your sig.

---

### Post by ZeroRider13 on 2011-01-22
> **kansasnoob said:**
> Aha:



So, go to Gparted, you'll likely have to click on the SWAP partition and select "swapoff", then "Create partition table". I'm guessing that the default will work with your machine.

But, **[COLOR="Red"]before that[/COLOR]**, post the output of:

```
free -m
```

If you have less than 512MB of RAM installation may be more problematic. Like you may have to reboot the Live USB before trying to install and bypassing the live desktop altogether.

      total       used       free     shared    buffers     cached
Mem:          1494       1160        334          0        136        680
-/+ buffers/cache:        343       1151
Swap:          377          0        377

-----------------------

that is free -m

Also if you don't mind giving me detailed instructions on how to do what you said please

also thanks kansas now i know where it is when i can

EDIT: No this is my old account and I have npt updated as of yet

There is an "extended" than "linux-swap" I right clicked the swap and pressed swapoff and the bar keeps moving back and forth but ti doesnt seem to be doing anything...

---

### Post by ZeroRider13 on 2011-01-22
So yeah, new info up there, also the swap wont go off, so if i right click on my 7.7gb i get format to: and options.  No create a partition table or anything, so how do i do that, or what do i format to?

---

### Post by kansasnoob on 2011-01-22
It sounds like you're going to have to swapoff and format that drive via command-line and I'm not sure how :(

Hang on and someone that does know will help you.

It looks like you have 1.5GB of RAM so running the Live CD should not be a problem.

---

### Post by kansasnoob on 2011-01-23
Arrgh, no one came along :(

I'm not at all proficient using fdisk but here's a guide:

[http://www.ehow.com/how_1000631_hard-drive-linux.html](http://www.ehow.com/how_1000631_hard-drive-linux.html)

Anytime I have to use fdisk I just have to Google for a guide. It's just not something I do often enough to commit it to memory.

---

### Post by kansasnoob on 2011-01-23
Oh, and I think you can just use:

```
swapoff -a
```

To turn the SWAP off. It may or may not require "sudo".

---

