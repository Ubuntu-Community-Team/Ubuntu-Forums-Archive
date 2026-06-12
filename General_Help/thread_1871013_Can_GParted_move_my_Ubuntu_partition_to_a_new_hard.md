---
title: "Can GParted move my Ubuntu partition to a new hard drive?"
date: 2011-10-28
forum: General Help
---

### Post by oscarivera9 on 2011-10-28
I have a PC with Windows 7, Ubuntu 11.10 and Mandriva 2011 installed on a 500GB hard drive.  I recently bought another hard drive, so now I want to keep Windows 7 on the first hard drive and move Ubuntu and Mandriva over to this new drive.  
Can I move my Ubuntu, and Mandriva partitions from one hard drive to the other with GParted?  I've moved partitions before, but only from within the same hard drive.
If there is an easier way to do this, I'm open to suggestions.  My main concern is Grub2 and making sure that I can still boot into all three operating systems.
If I need to I could do a fresh install of Mandriva, which is what I did just recently.  However, I would prefer to not have to do a fresh install of Ubuntu because I've had Ubuntu installed there since Natty.  I just recently did an upgrade from 11.04 to 11.10 and kept all of my settings after the upgrade.

---

### Post by dcstar on 2011-10-28
> **oscarivera9 said:**
> I have a PC with Windows 7, Ubuntu 11.10 and Mandriva 2011 installed on a 500GB hard drive.  I recently bought another hard drive, so now I want to keep Windows 7 on the first hard drive and move Ubuntu and Mandriva over to this new drive.  
Can I move my Ubuntu, and Mandriva partitions from one hard drive to the other with GParted?  I've moved partitions before, but only from within the same hard drive.
If there is an easier way to do this, I'm open to suggestions.  My main concern is Grub2 and making sure that I can still boot into all three operating systems.
If I need to I could do a fresh install of Mandriva, which is what I did just recently.  However, I would prefer to not have to do a fresh install of Ubuntu because I've had Ubuntu installed there since Natty.  I just recently did an upgrade from 11.04 to 11.10 and kept all of my settings after the upgrade.

Yes, just us the "Copy and Paste" functions in Gparted, then manually change the UUID of the copied partition (because it will be identical to the original).

Then update Grub and do a test boot of the new partition, and then delete the original partition when you are satisfied that the new one works 100% (and then update Grub etc.)

---

### Post by oscarivera9 on 2011-10-28
How do I manually change the UUID of the copied partition? and what do I change it to?

---

### Post by oldfred on 2011-10-28
Change UUID see also man pages:
uuidgen
sudo tune2fs /dev/sdaX -U numbergeneratedbyuuidgen
or:
sudo tune2fs -U random /dev/sdaX

You have to reinstall grub and edit fstab with the new UUIDs for both Ubuntu and your other install.

I believe in clean installs. Then you do not have UUID or grub issues. You can then just copy /home over and all your user settings will be restored. I actually now keep /home inside / (root) but have all data in either a NTFS shared partition for when I still had XP or an ext3 data partition. 

If you will only have Linux on the drive you may want to learn about gpt partitioning. Used by Macs and new windows computers with UEFI booting. Minor advantages as all partitions are primary and it has a backup of the partition table. With BIOS Windows will not boot from gpt but Linux does.
GPT Advantages srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)

---

### Post by oscarivera9 on 2011-10-30
OK
I know it's been a couple of days since I've posted anything here, but that's because work kept me busy and at the same time I was trying to educate myself on the possibility of using a GPT instead of MBR for my new disk as was suggested.  
I've read plenty to feel that I can go ahead and try to partition my second drive with GPT, however, I am concerned that if I have Linux on the new drive which will be partitioned with GPT I will NOT be able to boot Windows 7 even though W7 will be on the MBR disk.  One of the many things I read was that Windows 7 will not boot from a GPT disk unless I am using UEFI instead of BIOS.  My PC still uses BIOS.  I definitely need to boot from this new disk because that's where my Ubuntu installation will be, which is where my Grub 2 happens to be.
Is that correct?

---

### Post by oldfred on 2011-10-30
As long as Windows is on a MBR(msdos) disk and Ubuntu on the gpt disk you will not have problems.

I had a minor problem several versions ago as the gpt boot with grub2 did not recognized the BIOS partitions. They have since added that as part of all boots with grub. Windows does not see Linux partitions, but even if you put a NTFS partition on the gpt drive the BIOS based Windows will read it as I understand. Booting is the only issue.

I currently have Maverick in my gpt drive and boot XP on my BIOS drive.


I used gparted to set my drive as gpt. Device, create partition table and use advanced to change to gpt. Or you can use gdisk.

Since the BIOS Boot Partition ("bios_grub" flag set in GNU Parted) is used without a filesystem (no format) for storing GRUB 2 boot code "unknown" filesystem! may be shown in many Partition tools.

However, in the GPT setup, there is no space following the 512-byte MBR for embedding the "second stage" core.img. Thus, you must make a separate "BIOS boot partition" to hold core.img. You can set bios_grub flag in gparted (right click set flags) or with command line: In GPT fdisk (gdisk), give it a type code of EF02.
BIOS Boot Partition of 1 MiB for partition alignment.

sudo parted /dev/sda set <partition_number> bios_grub on

GPT fdisk Tutorial -srs5694 in forums
[http://ubuntuforums.org/showthread.php?t=1439794](http://ubuntuforums.org/showthread.php?t=1439794)
[http://www.rodsbooks.com/gdisk/](http://www.rodsbooks.com/gdisk/)
[http://www.rodsbooks.com/gdisk/download.html#obs](http://www.rodsbooks.com/gdisk/download.html#obs)

---

### Post by oscarivera9 on 2011-10-31
> I currently have Maverick in my gpt drive and boot XP on my BIOS drive.
That answers lots of my questions.
Thank you very much for your help oldfred, you've given me lots of insight. lots of answers & lots of new questions that originated from your answers.  I think I will now go ahead and get started with the process.  It's good to know that in the Linux community we've got tons of great support from each other.
The only negative thing that came out of this whole scenario was finding out through my outside readings about Micro$oft's evil plans to get rid of their #1 enemy (Linux) through "secure boot" being included in the UEFI specifications.  Supposedly, less than 2% of all desktop users use Linux, but I strongly think that the percentage is  much higher and the potential for growth is the main reason why Micro$oft wants to get rid of Linux, because they know that it's only a matter of time before we outnumber them.  So they need to act now, while they can still 'strong-arm' anyone who poses a serious threat.

---

### Post by oldfred on 2011-10-31
Glad I could help.

If you have new questions, it is usually best to start a new thread with appropriate title to get those who know about an issue to look at it.

---

