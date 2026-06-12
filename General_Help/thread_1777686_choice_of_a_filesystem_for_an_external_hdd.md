---
title: "choice of a filesystem for an external hdd"
date: 2011-06-08
forum: General Help
---

### Post by PeterP24 on 2011-06-08
Hi,

I just bought a new external hdd. It came with a fat32 file system or something like that. I would like to format it using a more modern file system. I would prefer, if possible, to avoid the ntfs option at risk of not being able to connect the external hdd to the windows boxes. I would consider ntfs though if it will be proven to be more reliable and secure than the linux alternatives. My question is: what is the most reliable and secure (against file corruption or file loss) file system for an external hdd? Or at least what are the top options. I would also like to be able to secure my data on the hdd by encrypting the whole hdd - but this may be another issue. 

Best regards,

pts

---

### Post by PeterP24 on 2011-06-08
I just decided to try the ext4 file system and guess what: about 70 GB storage space are lost. To give more details: about 15 GB are not seen (instead of reporting 931 GB it reports 916 GB) while the rest are reported as occupied (although the hdd is newly formatted). 

I tried xfs also but it didn't work: some weird errors are thrown. NTFS works as expected (931 GB are found and reported) - but when removing the hdd through "Safely remove drive" option another error is thrown (I found it here: [http://ubuntuforums.org/showthread.php?t=1487620&highlight=unable+to+stop+drive](http://ubuntuforums.org/showthread.php?t=1487620&highlight=unable+to+stop+drive) it appears to be an Ubuntu bug). Any idea would be appreciated.

pts

---

### Post by mastablasta on 2011-06-08
Ubuntu gives you gigabytes (GB) or gigibytes (GiB)?
 
you first post is confusing. EXT file system can not be read by Windows (unles you use some tools) while NTFS can be read by Windows and it stable as far as i know it. so if you ever plan on using this disk on windows it will have to be NTFS.
 
Also you might need to propperly align the partitions if you have "advanced format" disk.
 
---
[https://wiki.ubuntu.com/LucidLynx/ReleaseNotes](https://wiki.ubuntu.com/LucidLynx/ReleaseNotes)
**Partition alignment changes may break some systems**
 
 
By default, Ubuntu 10.04 LTS aligns partitions on disk to 1 MiB (1048576 bytes) boundaries. This ensures maximum performance on many modern disks, particularly solid state drives but also new "Advanced Format" disks with physical sectors larger than the traditional 512 bytes. Very few systems nowadays need the old alignment, used in the days of MS-DOS when it was useful for partitions to start at the beginning of a cylinder. In some rare cases, optimal alignment may cause problems. Some BIOS implementations (those on Asus P5P800-MX and Asus P5GZ-MX motherboards) have been reported to hang after installation. It may be difficult to install Microsoft Windows XP and older after installing Ubuntu, although more recent versions of Windows should be compatible with optimal alignment and indeed may produce it themselves. If you find that you need to use the old cylinder alignment instead, then add the partman/alignment=cylinder boot parameter when starting the installer. ([551965]("https://bugs.launchpad.net/bugs/551965"))

---

### Post by PeterP24 on 2011-06-08
Sorry about confusion. I am using using exclusively Ubuntu - I don't have Windows and I don't intend to use it or to connect my hdd to an Windows box in the future. I am aware that if I will format my external hdd to a nonWindows file system I would not be able to use it on Windows.

I just checked and ubuntu reports the storage capacity in GB. Right now I have it NTFS formated using Ubuntu tools and it reports 931.4 GB. I am pretty confident that this value is ok since I read some reviews of this particular hdd and this value was reported also by users that had windows as their OS. When I started the thread I didn't wanted to have NTFS since I hoped I could use some Linux alternatives. Meanwhile I discovered that there is an annoying bug related to NTFS - I have to use some terminal command to safely remove the drive instead of doing it with right click like everybody else.  
I will check the link you provided. Also, thank you for mentioning GiB - I wasn't aware that there is another unit of measure for storage capacity besides GB.

pts

---

### Post by coldraven on 2011-06-08
I have a 1TB Samsung Story external USB drive.
I formatted it to NTFS and I have had no problems, it unmounts with right click or in Nautilus just click on the "up arrow" next to the drive name.
It is useful because I can take it to friends houses and copy direct to their Mac or Windows machines. Some of my files are bigger than 4GB so it saves me burning a CD or DVD.

---

### Post by PeterP24 on 2011-06-08
> **coldraven said:**
> I have a 1TB Samsung Story external USB drive.
I formatted it to NTFS and I have had no problems, it unmounts with right click or in Nautilus just click on the "up arrow" next to the drive name.
It is useful because I can take it to friends houses and copy direct to their Mac or Windows machines. Some of my files are bigger than 4GB so it saves me burning a CD or DVD.

Well - I have two external hdd (NTFS) and I use them in the same way you use yours. I don't need a third one formatted to NTFS - this last one is intended to backup some personal data I don't want to share with others. Like I said in a previous post, although I initially intended not to, I have it NTFS formated right now (at least temporarily) - and when I unmount it it gives me an annoying message - something about being unable to remove the drive - for which I have an workaround. I didn't intend to question the NTFS file system usability. All I wanted was to use an alternative like ext4 or xfs or whatever was better (I still want).

pts

---

### Post by Bitrate on 2011-06-08
> **PeterP24 said:**
> I just decided to try the ext4 file system and guess what: about 70 GB storage space are lost. To give more details: about 15 GB are not seen (instead of reporting 931 GB it reports 916 GB) while the rest are reported as occupied (although the hdd is newly formatted). 

pts


You can alter the amount of reserved space ext4 uses on a hard drive partition by using the tune2fs command:

eg. To reclaim all disk space for data storage use this command:

sudo tune2fs -m 0 /dev/sdxx (where xx= drive type and letter).


NB: This example should only be used on a storage drive. A bootable drive will need free space for ext4 journaling. Changing the value '0' to something like 2 or 4 is a reasonable value for a bootable drive.

---

### Post by psusi on 2011-06-08
> **Bitrate said:**
> You can alter the amount of reserved space ext4 uses on a hard drive partition by using the tune2fs command:

eg. To reclaim all disk space for data storage use this command:

sudo tune2fs -m 0 /dev/sdxx (where xx= drive type and letter).

It isn't good to completely fill the disk anyhow, so it is best to just leave the reserved space alone and not worry about it.

> **Bitrate said:**
> NB: This example should only be used on a storage drive. A bootable drive will need free space for ext4 journaling. Changing the value '0' to something like 2 or 4 is a reasonable value for a bootable drive.

The journal and the reserved space have nothing at all to do with each other.  The journal is permanently allocated when you format.

---

