---
title: "External hard drive questions"
date: 2010-06-01
forum: General Help
---

### Post by Cuddles McKitten on 2010-06-01
Here's my situation: I'm looking to buy my first external hard drive for data backup for my laptop.  I've never used one before and have virtually zero knowledge on them.

1. If I want data backup, is an external HD the best route to go for on-site access?

2. Am I correct in assuming that virtually any popular external hard drive on the market will work well with Ubuntu or should I look to certain types only?

3. Assuming that I just copy a few GB of data onto them every week or two, about how long should I be able to expect the HD to continue to function?

4. Stupid question, but I still must know.  I'm assuming I can use an external hard drive like a flash drive and install an OS to boot off of.  How much slower would it run compared to off my internal HD?  How much would it reduce the lifetime of said external HD?

---

### Post by Cuddles McKitten on 2010-06-01
Bueller?

---

### Post by john newbuntu on 2010-06-02
You should be able to find a lot of info on these on the internet. Here's my take:

1. External HDD are convenient but might not be as fast as internal HDDs.  eSATA drives are faster than the USB and firewire ones if your computer supports that interface.  Yes they offer excellent on-site backups for home computers, especially when you have just a few computers and do not want to go for SAN or NAS type solutions involving more setups and maintenance.

2. As for support by HDD manufacturers, some do not support linux/ubuntu or at least do not mention it in their warranty.  Most offer some kind of built-in software that run well on Windows or Mac and not on Linux.  If you are interested in partitioning or installing linux on some of these, it might not work.  Case in point - Samsung s1 mini - ( [http://ubuntuforums.org/showthread.php?t=1252729&page=2](http://ubuntuforums.org/showthread.php?t=1252729&page=2) ) or WD my passport and its smartware software removal).  Before you buy, google and figure out if people are having problems with the drive in installing your favorite distro.

3. Hard to tell how long they will last.  They do have high MTBF's like the internal ones. I have heard of a few drives failing in a month or so. I have been using mine (Transcend 25M) for about an year now with no problems and a friend of mine has had a WD passport working just fine after almost 2 years.

4. Yes, it is like a flash drive. You may require a power connection on some while some others might require an extra USB port for power.
On most, you should be able to blank the drive and repartition/format and work on it just like an internal drive.  But please check this before you buy.  Windows, as far as I know will not boot from an external drive unless you work around it like remove your internal HDD. Linux/ubuntu has no such problems.  I have a cloned ubuntu install running on my external hdd, with grub on its MBR. It is about four to six times slower than my internal one obviously because of the USB 2.0 bottleneck.  You might want to consider a drive that supports USB 3.0 just in case.

---

### Post by inameiname on 2010-06-02
Most usb external drives work just fine on Linux, whether they specifically say they run on Linux or not. Guess they just forget we exist. :P And as the above reply says, the software that comes preinstalled on them probably wouldn't work. Personally though, I never use that stuff and just erase it anyway.

---

### Post by leg on 2010-06-02
Most external HDs will be fine and connected through USB will work well but will be a little slower. Neither Windows or Linux machines will have any problems accessing them but you should should make sure that you format it with fat32 if you do intend to access it from both. I also wouldn't install an OS on there if you want to back up data as you can use the OS of the machine that has the data to back up and use the extra space for backing up.

---

### Post by JoelOl75 on 2010-06-02
I've encountered higher failure rates in external drives simply because of "Movement" while in operation.  They shouldn't be fire up then dropped on a table or flipped around while in operation... otherwise they will live a long life.  Some enclosures are not all that great at dissipating heat so long term 24/7 use may contribute to shorter life for cheap ones with no fan and a plastic enclosure. Aluminum enclosures and fan cooled ones seem better (I put together my own external USB drives by using a 3.5" drive and a separate case).   The type of drive has alot to do with the heat output.  I recommend Western Digital Caviar Green 1.5T drives as they offer great size and price with low power/heat production as they are variable speed 5400rpm drives and more than adequate for USB 2 speeds.

ESATA can be finicky with hot plugging but are faster.  The new USB 3 is alot faster and moves the bottleneck back to the drive and is the way to go if you can! Even adding a PCI-E card for USB3 support is do-able but I'm getting off topic.  Asus makes a add on USB3 card that also has SATA 6.0Gb controller all in one Check out this enclosure!  [http://www.legitreviews.com/article/1308/1/](http://www.legitreviews.com/article/1308/1/)

And here's the card:
[http://www.newegg.com/product/product.aspx?Item=N82E16813995004](http://www.newegg.com/product/product.aspx?Item=N82E16813995004)

If you are backing up Linux files (Not just media, but system backups) DON'T USE FAT32!  Don't use NTFS either.... I would recommend Ext4.  FAT32 and NTFS don't preserve user/group names and other UNIX acls.  Also FAT32 can't store files larger than 2GB.

For small drives or thumb drives use Ext2 as the Journal isn't a great benefit at these smaller speeds, while larger drives (say greater than 30GB) will take longer to fsck with Ext2 so I'd use Ext4.

If all you do is store large files (Movies/Music) on the external drive I would use XFS.  XFS is a great filesystem for this but you MUST not have itchy fingers and unplug your external drive without properly unmounting a XFS drive.... (Although you SHOULD always properly unmount the drive no matter what FS you pick)

If it's going to be shared with Windows boxes then I guess your stuck with FAT32 or NTFS but remember the drawbacks.  If you want to back up both types of systems to the same drive you can always partition it and use a combo of filesystems if needed.  Better to just get another drive though and keep each dedicated to each system.  I don't use Windows so I have no need to use Fat/NTFS and I recommend not using FAT or NTFS if you don't need to.

There's also self powered USB enclosures that house a 2.5" laptop hard drive.  These are nice and compact but sometimes are problematic as they draw near the limit of power that's available on the USB bus (5v 500mA) and some USB ports on some computers just arn't up to snuff.  All 3.5" cases are external powered (less convenient with another cable to hook up)

Hope this helps!

---

