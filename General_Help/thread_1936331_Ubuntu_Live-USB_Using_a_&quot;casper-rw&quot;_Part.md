---
title: "Ubuntu Live-USB Using a &quot;casper-rw&quot; Partition"
date: 2012-03-05
forum: General Help
---

### Post by HappyJony on 2012-03-05
Let me start by saying that this is my first post - ever - and that I have been using Ubuntu for about 2 years without the need to directly ask any questions on any forum whatsoever. If my thread is in the wrong section then I apologise in advance.

I've been trying to turn my lexar v.10 16gb usb stick into a persistent live-usb that uses an ext2 partition instead of the usual caper-rw file to use the space on my drive to its full extent. I'm using Ubuntu LTS 10.04. I was able to get my hands on two pages that explain how to do it:

[http://www.pendrivelinux.com/create-a-larger-than-4gb-casper-partition/](http://www.pendrivelinux.com/create-a-larger-than-4gb-casper-partition/)

When I did it the way that the website suggested, the OS on the pendrive ran extremely slow. I have also an old 4gb stick, and Ubuntu would run significantly faster. The transfer rate on the new 16gb flash drive is much higher, I've checked.

[http://ubuntuforums.org/showthread.php?t=1629477](http://ubuntuforums.org/showthread.php?t=1629477)

Poster #6 gives out a way to pull it off but the last part isn't quite clear:
"Select disk / syslinux / text.cfg and added "persistent" as shown below:
append noprompt cdrom-detect/try-usb=true persistent file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.gz quiet splash --"

No matter how I modify the "text.cfg", it won't work at all. Most of the time the live-usb isn't even persistent after I modify the file but I've had it crash entirely too.

Thanks in advance,
Jony

---

### Post by HiImTye on 2012-03-05
just use this [guide]("https://wiki.ubuntu.com/LiveUsbPendrivePersistent"), using 'Method 0'
it will run slower than if it weren't a liveCD as it is limited to USB speeds. using a swap drive on a hard disk may help but then why would you be using a persistent LiveCD?

you will find better speeds with ext4 but in order to gain the speed advantage of ext3/4 (journaling) you will reduce the life of your flash drive (as journaling requires more writes). not using a journaling file system also comes with an increased risk of the partition being unusable if the system fails (but it is minute). it also means that you will need to wait longer for file system checks.

(FYI, I use ext4 on my persistent install, which I have allocated 3GB to - the size of the base install on a FAT32 filesystem and then the remainder in an EXT4 partiton. the rest of my drive is a FAT32 storage partition, which I use for transferring files between computers (and in the LiveCD session))

---

### Post by HappyJony on 2012-03-05
Method 0 is the same as the method given in the first website that I visited. Here's the issue with this method that I'm having:

Old usb:
-4gb
-faster at running the OS compared to the new usb
-persistent Live-USB, uses the casper-rw _file_
-data transfer: 15 MB/s Read; 4 MB/s Write

New USB:
-16gb
-irritatingly slow, it took me about 15 min to install chromium: running on a dual core laptop with 3 gb of ram.
-persistent live-usb, uses a casper-rw _partition_
-transfer rate: 28 MB/s Read; 10 MB/s Write

I suppose that I didn't think about this, but could it be that using a casper-rw partition is slowing things down? BTW, I did try using an EXT4 partition, no changes to the speed as far as I could tell. 

I've been at this since yesterday, its nice to have such a fast reply. Thanks!
Jony

---

### Post by HiImTye on 2012-03-06
are those your theoretical transfer rates or the rates you are actually attaining?
it could be that your computer is using USB 1.0 instead of 2.0 but it is more likely the drive itself, some flash drives are just faster than others. theoretically, an ext4 partition will be faster than a FAT32 partition, and a large file as a simulated partition might slow things down even further. an ext2 partition should be comparable to a FAT32 partition. I would try running the LiveCD without casper and seeing if you experience the same slowness

---

### Post by dcstar on 2012-03-06
> **HiImTye said:**
> are those your theoretical transfer rates or the rates you are actually attaining?
it could be that your computer is using USB 1.0 instead of 2.0 but it is more likely the drive itself, some flash drives are just faster than others. theoretically, an ext4 partition will be faster than a FAT32 partition, and a large file as a simulated partition might slow things down even further. an ext2 partition should be comparable to a FAT32 partition. I would try running the LiveCD without casper and seeing if you experience the same slowness

The **last** thing you want to do with any USB "Stick" partiton is use a Journaling filesystem. EXT4 is a Journaling filesystem. Use EXT2.

---

### Post by HappyJony on 2012-03-06
Those are the speeds that I got are from websites. The speeds don't really matter; Based on the simple premise that my old usb is a cheap one that I bought about 2 years ago and the new one is a pretty good one, the new should be faster than the old. But that's not the real problem.

As for whether its a usb 1.0 or 2.0, I already gave out the specs lol. I don't even need to check its a laptop with vista on it, its not old at all.

Here's my speculation: using an ext2 partition instead of a casper-rw **file** slows down the speed severely. Now the question is, is this to be expected or is something amiss? I'm getting serious lag loading internet pages, its not normal.

[QUOTE=dcstar]The last thing you want to do with any USB "Stick" partiton is use a Journaling filesystem. EXT4 is a Journaling filesystem. Use EXT2.[/QUOTE]

+1, I just had to try it to see if it would change something.


Jony

---

### Post by dcstar on 2012-03-08
> **HappyJony said:**
> 
.......
Here's my speculation: using an ext2 partition instead of a casper-rw **file** slows down the speed severely. Now the question is, is this to be expected or is something amiss? I'm getting serious lag loading internet pages, its not normal.
.......

AFAIK the casper-rw file is a Write-only file that will eventually run out of space because it is designed to reduce the impact on USB "Stick" drives by only ever using the same space once. Every time you delete or re-write data you lose free space.

A normal partition won't have this issue, but the work required to rewrite blocks on a USB stick is considerable more than just grabbing free blocks to write to - that is probably where the speed issue becomes apparent. As well the constant writes on the same location on a USB stick will kill it off quite quickly.

---

### Post by HappyJony on 2012-03-08
So you're saying that this should be the other way around? I should get an increase in speed if I'm using a partition instead of the file?

Jony

---

### Post by oldfred on 2012-03-08
If you have a 16GB flash drive, why not a full install? I have 12.04 running on my 16GB flash with an 8GB / (root) partition just to test that it works on my portable system. I used gpt partitioning, formated to ext4 but turned off journal and made a few settings to reduce writes. It is only a few seconds slower booting, seems a bit slower in loading a larger app like Firefox but once running I really cannot tell a difference with my hard drive. I have no swap and only 1.5GB of RAM so I am careful not to load more than one main app.

It does not have to be encrypted BIOS based system:
Standard full install with screenshots to flash or SSD:
Ubuntu Encrypted Flash Memory  Installation
[http://members.iinet.net/~herman546/p19.html](http://members.iinet.net/~herman546/p19.html)
More discussion Dec 2010, more SSD info
[http://ubuntuforums.org/showthread.php?t=1643591](http://ubuntuforums.org/showthread.php?t=1643591)
[http://ubuntuforums.org/showthread.php?t=1404664](http://ubuntuforums.org/showthread.php?t=1404664)

How to Tweak Your SSD in Ubuntu for Better Performance
[http://www.howtogeek.com/62761/how-to-tweak-your-ssd-in-ubuntu-for-better-performance/](http://www.howtogeek.com/62761/how-to-tweak-your-ssd-in-ubuntu-for-better-performance/)
See comment: There’s no reason to use BOTH noatime and nodiratime, using noatime implies nodiratime.

BIOS settings (SSD but also most systems)
[http://www.ocztechnologyforum.com/forum/showthread.php?79848-THE-BASIC-GUIDE-amp-FAQ-ABC-for-OCZ-SSD&p=567561&viewfull=1#post567561](http://www.ocztechnologyforum.com/forum/showthread.php?79848-THE-BASIC-GUIDE-amp-FAQ-ABC-for-OCZ-SSD&p=567561&viewfull=1#post567561)

Use ext2 or ext4 without journal:
sudo tune2fs -O ^has_journal /dev/sda1
sudo tune2fs -o discard /dev/sda1
No swap or set swapiness or install 'Dynamic Swap Space Manager' from the Ubuntu Software Center
After installing, change the fstab so that everything gets mounted with noatime.
change to noop i/o scheduler

---

### Post by HappyJony on 2012-03-08
Thanks for the reply Fred, I know I'm going to be tweaking my flash drive for better performance:D

[QUOTE=oldfred]sudo tune2fs -O ^has_journal /dev/sda1
sudo tune2fs -o discard /dev/sda1[/QUOTE]
I understand the rest of that paragraph, but I'm not sure what you mean in this specific part.

Since I'm about to embark into this, I'd like to ask: Can I upgrade my kernel if I do a full install? I'm using the olde LTS, and its not digesting very well one of our newest laptops at home.

Thanks again,
Jony

---

### Post by oldfred on 2012-03-09
Someone suggested that ext4 without journal is still better than ext2. The first command turns off the journal. 

There seems to be several ways to set the discard parameter. there is another one:
Alternate to discard, call fstrim via cron
[http://opensuse.14.n6.nabble.com/SSD-detection-when-creating-first-time-fstab-td3313048.html](http://opensuse.14.n6.nabble.com/SSD-detection-when-creating-first-time-fstab-td3313048.html)

I am testing 12.04 on my 8GB partition on the 16GB flash. It is a full install and everything works just like an install to a drive. Kernel updates are no different.

---

### Post by C.S.Cameron on 2012-03-09
> No matter how I modify the "text.cfg", it won't work at all. Most of the time the live-usb isn't even persistent after I modify the file but I've had it crash entirely too.


In the years I have been visiting this forum I have never read of anybody bricking a flash drive running Ubuntu from it, Journaling or not.

10000 writes at 10MB/s takes a long time on a 16GB flash drive.


Another method to setup with persistent partitions is to format FAT32 and ext2, (casper-rw), partitions, install to the FAT partition using Startup Disk Creator with minimum persistence and then delete the casper-rw file.

---

