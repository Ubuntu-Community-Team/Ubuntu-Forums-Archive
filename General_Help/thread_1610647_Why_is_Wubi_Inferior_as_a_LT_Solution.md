---
title: "Why is Wubi Inferior as a LT Solution"
date: 2010-10-31
forum: General Help
---

### Post by onaridge on 2010-10-31
Why is wabi not considered a long term solution for using Ubuntu next to Windows? So far I have virtualized 10.10 and 10.04 and wabi'd 10.04. The Wabi install worked the best with NO issues but I keep hearing that it isn't a long term solution. I am a little scared of the dual boots just yet as I don't want to hose my Windows installation by doing something wrong in the partitioning process, and I am working off a virtual CDROM too which makes it a little trickier I think. I might not be able to access the recovery partition if I do something dumb.

---

### Post by 3rdalbum on 2010-11-01
If Windows crashes and won't boot, then Ubuntu won't boot either. You are restricted in the amount of space you can allocate for Ubuntu. If it works as it is right now then stick with it, but a real dual boot doesn't have the restrictions.

---

### Post by beew on 2010-11-01
It is actually WUBI not Wabi. But anyway, WUBI is a windows program running from a Windows folder. Its existence depends on Windows, this is not giving Ubuntu its due. WUBI is for trying out Ubuntu, it is not a real install, it doesn't have full control as a real OS.

---

### Post by oldfred on 2010-11-01
The designer of wubi does not think it is long term.

[http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/](http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/)
Agostino: Wubi actually wasn’t designed to do long-term installations. The main aim was really to let people try out Ubuntu with confidence. Normally, users that start with Wubi tend to upgrade to a full installation to a dedicated partition at the next release cycle.

---

### Post by PhilGil on 2010-11-01
The biggest problem I see with a long-term WUBI install is the vulnerability of the single file. If it gets corrupted your Ubuntu install is toast, and you don't have the ability to boot from a live disk to repair the system or recover your files.

---

### Post by onaridge on 2010-11-01
Ok thanks for the info.....I was not happy with my virtual installs because my network was hit or miss, but am a little nervous about messing around with partitions just yet for a dual boot. I will read up as much as I can and then take the plunge later.

---

### Post by 3Miro on 2010-11-01
WUBI lives on an NTFS file system which is not nearly as good as the default Ubuntu ext4.

For the partitions, do as much of the work as possible under Windows. Then on the advanced HDD settings of the Ubuntu installer you will just select partitions to format and use. This is probably the safest way (even though I have resized windows partitions form Ubuntu live CD without trouble).

---

### Post by onaridge on 2010-11-01
I think the thing that is really holding me back is the fact that my laptop has no crdom and everything I have read has said have a backup recovery cd at hand just in case. How can I recover from a problem without that cd? I have two external hard drives but not sure how they might be used to remedy a corrupt system that won't boot.

---

### Post by 3rdalbum on 2010-11-01
> **onaridge said:**
> I think the thing that is really holding me back is the fact that my laptop has no crdom and everything I have read has said have a backup recovery cd at hand just in case. How can I recover from a problem without that cd? I have two external hard drives but not sure how they might be used to remedy a corrupt system that won't boot.

How do you live without an optical drive? In any case you can get external drives, or here's a tip: If you have only an internal drive, you can get an adapter that converts it into an external drive. You don't need the full enclosure, just a little circuit board with a USB plug and SATA plug and a power brick.

---

### Post by Jay Car on 2010-11-01
If your computer has USB, you can always try this: [Installation From USB Stick]("https://help.ubuntu.com/community/Installation/FromUSBStick").

---

### Post by onaridge on 2010-11-01
Well, I have a Dell XPS system with two DVD drives etc, and that has a full 10.04 installation only. I love it so much that I now want to make my laptop Ubuntu as well but still want to keep Windows for a few things. Up until now I really didn't see the need for external drives and I wanted something small (it's 13 inch). Now that I have fallen in love with Ubuntu, I want it everywhere! :-)
Jay, my biggest concern was being able to reinstall Windows if necessary and that I can't do from a USB drive or can I? 
The USB drive is the way to go then for Ubuntu install...but will there be a way to reinstall windows if there is a catastrophe or if i can't boot?

---

### Post by cpmman on 2010-11-01
If you click on the WubiGuide in my signature there is a number of different ways to re-organise a Wubi install by extending partitions/separating partitions/migrating to full dual boot.

**BUT**: a backup is always advisable.

---

### Post by onaridge on 2010-11-01
LVPM currently does not work with installs generated by Wubi 10.04, and that's what I would want to use :-((

---

### Post by philinux on 2010-11-01
> **onaridge said:**
> Why is wabi not considered a long term solution for using Ubuntu next to Windows? So far I have virtualized 10.10 and 10.04 and wabi'd 10.04. The Wabi install worked the best with NO issues but I keep hearing that it isn't a long term solution. I am a little scared of the dual boots just yet as I don't want to hose my Windows installation by doing something wrong in the partitioning process, and I am working off a virtual CDROM too which makes it a little trickier I think. I might not be able to access the recovery partition if I do something dumb.

When the Wubi instal gets a grub update it borks the windows bootloader. Result is windows won't boot and a mbr recovery is needed.

---

### Post by sidzen on 2010-11-01
Linux all the way.  Who needs wubi?

---

### Post by onaridge on 2010-11-01
> **philinux said:**
> when the wubi instal gets a grub update it borks the windows bootloader. Result is windows won't boot and a mbr recovery is needed.
ouch!

---

### Post by cpmman on 2010-11-01
Sorry - this one works for some:

***_[http://ubuntuforums.org/showthread.php?p=9476897#post9476897]("http://ubuntuforums.org/showthread.php?p=9476897#post9476897")_***

---

### Post by philinux on 2010-11-01
> **onaridge said:**
> ouch!

Some other ouches.

[https://wiki.ubuntu.com/WubiGuide#Troubleshooting](https://wiki.ubuntu.com/WubiGuide#Troubleshooting)

---

### Post by onaridge on 2010-11-01
actually wubi was pretty flawless and quite snappy except at the very beginning when I had authentication lags. But it's obvious now it's not a long term solution. I am gathering up the things I need for the dual partition. I will purchase a flash drive tomorrow. As far as windows goes, if it gets hosed I guess I take the laptop to the local guru and have him reinstall the Windows part. The funny thing is I will probably end up using Ubuntu exclusively soon after. :-)

---

### Post by oldfred on 2010-11-01
If you do not have a CD drive you need several USB flash drives. You can copy the windows repair CD to a flash drive so you can repair your windows. Easier to do from windows while it is working. I then also have a USB flash drive of several linux liveCDs, Ubuntu, system rescue, parted magic etc, which let me boot and repair Ubuntu, most XP issues and some Vista/7 issues. With grub2 you can put them all one one Flash drive and loop mount them but that is after you have learned how to do each one first.

If your PC did not come with a complete Vista or Win7 installation CD, you can download a Recovery Disc at the following links:
Windows Vista/7 Recovery Disc - for repairs only
[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)
Vista will not repair XP (they create the boot sectors differently) but can run chkdsk.
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

---

### Post by bcbc on 2010-11-01
> **onaridge said:**
> LVPM currently does not work with installs generated by Wubi 10.04, and that's what I would want to use :-((

Here's a howto including an updated script to migrate a wubi install. [http://ubuntuforums.org/showthread.php?t=1519354](http://ubuntuforums.org/showthread.php?t=1519354)

---

### Post by bcbc on 2010-11-01
> **onaridge said:**
> actually wubi was pretty flawless and quite snappy except at the very beginning when I had authentication lags. 

Yes, wubi works fine, despite some of the sensationalist comments here... it has its problems, and is not intended for long term use, but rocks when compared to a virtual machine or live CD/USB. As long as you keep in mind that it's not forever (make sure your data is secure) it's safe to use it. Just don't upgrade or go crazy - like install burg :)

And PS if you get a grub-pc update, it won't automatically scrub your MBR - it will ask you politely whether you'd like to do it*. Just don't install it anywhere and you'll be fine.

* under certain conditions - when wubi is installed to a different partition than windows. 
PS this bug affected normal Ubuntu installs too, until it was fixed. Just the developer can't figure out how to fix it for the wubi different partition scenario.

---

### Post by onaridge on 2010-11-01
Nope, no installation cd's came with Windows 7 so I will buy a few flash drives (2G each?), and copy that recovery cd disk.  Thanks...you have made it possible for me! :-) and I am downloading the recovery iso as I type.

---

### Post by onaridge on 2010-11-01
> **bcbc said:**
> Here's a howto including an updated script to migrate a wubi install. [http://ubuntuforums.org/showthread.php?t=1519354](http://ubuntuforums.org/showthread.php?t=1519354)

Thanks BC I will save this.

---

### Post by uRock on 2010-11-01
Wubi is great for getting the feel of the system before running a full install. It is nice to be familiar with the OS before getting it installed and trying to figure out where things are while getting drivers and such installed.

The good side to Wubi is that you can boot Windows and defrag, whereas with Linux file systems you do not have any simple defrag tools.

---

### Post by onaridge on 2010-11-01
I just realized, I have FOUR partitions already on my HP hard drive. C which is 278.79G and NTFS; HP Tools 99mb, Fat32; Recovery NTFS, 19G; and System, NTFS, 199MB. Since I can only have 4 partitions what do I do? Do I really need HP tools? If I got rid of HP tools then the unallocated space from the windows shrink would give me the ability to add the 3 logical partitions for Ubuntu correct?

---

### Post by Lancro on 2010-11-01
I did the bcbc script, I first tried ubuntu with wubi, I loved it, and I take a partition for it, I moved my wubi install to a partition, and deleted the wubi system, now I use grub, windows partition wont be damaged if you resize the partition with windows, and you can always do a bootrec /fixboot and /fixmbr to delete grub, but as you get in love with ubuntu you wont use windows...

---

### Post by oldfred on 2010-11-01
Beside the tools which you should backup anyway, you can also delete the recovery. It usually gives you a chance to burn 1 or 2 recovery CD/DVDs that are not really install CDs, but just images of your drive as purchased. I would never want to go back to like new as I have made too many changes, but you should have the CD/DVD just in case. Then you could delete that one also.

---

### Post by Lancro on 2010-11-01
> **onaridge said:**
> I just realized, I have FOUR partitions already on my HP hard drive. C which is 278.79G and NTFS; HP Tools 99mb, Fat32; Recovery NTFS, 19G; and System, NTFS, 199MB. Since I can only have 4 partitions what do I do? Do I really need HP tools? If I got rid of HP tools then the unallocated space from the windows shrink would give me the ability to add the 3 logical partitions for Ubuntu correct?

3?, I have 2 partitions only for ubuntu, swap and ext4.

---

### Post by oldfred on 2010-11-01
Two partitions work, but if you plan on new installs rather than upgrades having /home as another partition can be an advantage.

I only had two partitions for Ubuntu for several years. I also had a shared NTFS and an XP install. But when I decided I wanted a new clean install to houseclean out the several years of cruft, I converted to a separate /home and then to /data and additional partitions for more roots so I could have several installs. (New hard drive with lots of room helped).

---

### Post by wilee-nilee on 2010-11-01
Since you have external HD's use the W7 backup utility. You can back up the whole W7 image and all the extras in one fell swoop that can be reimaged using the recovery disc. Just look at the backup program carefully and make sure you understand it. I would call the manufacturer, I suspect a full install dvd or the oem set is available for a couple of bucks. Mine for XP from acer was 20$ US

I used this just a couple of days ago to reset a W7 that had been tweaked to not getting to the net anymore. Nothing like a little fun to get you in trouble,the image slid back in with no problems. The image though was of the same sized partition that I put it back into, I did this with maverick still in place with no change of the bootloader.

I would do two images if it was me the original as it is and one of the final version. The first I believe would want to have the 4 partitions.

Lots of good help on the thread good luck.;)

---

### Post by onaridge on 2010-11-01
Yeah I like the idea of having home as a separate partition.

I priced out portable optical drives and heck I can get one for $18 so I will get one to use with the laptop, make my recovery disks for Windows and off I go to dual boot land.

---

### Post by onaridge on 2010-11-01
Willee, Yes all 4 partitions. Good idea and I will find how much a disk would be from HP. No mater how hosed the PC gets including if I delete the recovery partitions, the disk will autorun and put back the Windows image?

---

