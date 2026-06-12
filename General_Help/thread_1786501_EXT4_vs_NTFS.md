---
title: "EXT4 vs NTFS"
date: 2011-06-19
forum: General Help
---

### Post by subchief on 2011-06-19
Hey guys,
i have recently migrated from windows to ubuntu as the only operating system on my computer. I have several partitions on my hard disk and except the filesystem partition, the rest are in ntfs format. What would you advice:
1 Should i convert them from ntfs to ext4 or not?
2 what are the advantages of ext4 over ntfs?

Thanx

---

### Post by lemonchicken on 2011-06-19
I've experienced 70-90mbps transfer speeds with ext4/ubuntu  against 40-60mpbs ntfs/windows [same drive]
ext4 imo is a definite for running ubuntu..

---

### Post by coffeecat on 2011-06-19
If you are not running Windows on that machine it would be inadvisable to keep a partition formatted NTFS. If the filesystem were to become damaged, it would need Windows' chkdsk to repair it. Linux tools for NTFS are not as comprehensive. For an Ubuntu-only system I would use ext3 or ext4 only.

---

### Post by subchief on 2011-06-19
> **lemonchicken said:**
> I've experienced 70-90mbps transfer speeds with ext4/ubuntu  against 40-60mpbs ntfs/windows [same drive]
ext4 imo is a definite for running ubuntu..

How about stability,integrity of files etc?

---

### Post by nrundy on 2011-06-19
Read this to find out the differences:  [http://www.pcworld.com/businesscenter/article/230527/ubuntu_linux_day_16_ext4_vs_ntfs.html](http://www.pcworld.com/businesscenter/article/230527/ubuntu_linux_day_16_ext4_vs_ntfs.html)


In real world usage the big thing you will notice when comparing NTFS to Ext4 is that Ext4 will not deteriorate in performance with time. You can install and then use for several years with hardly any deterioration in performance.

With NTFS, you really should reformat and reinstall the OS about once a year because with continued use performance continues to decline. I've had Windows XP installs that moved at a snails pace after running for 3 years. A reformat and reinstall and it was snappy again for a little while.

---

### Post by Enigmapond on 2011-06-19
> **subchief said:**
> How about stability,integrity of files etc?

Better, IMHO as ext4 handles data in a more organized way but as stated above, if you are not sharing a partition with Windows it is not advisable and not much point to keep the NTFS and I would suggest re-formatting to ext4.

---

### Post by lemonchicken on 2011-06-19
> **subchief said:**
> How about stability,integrity of files etc?

I think stability and integrity are involved with the quality of hard  drive. I don't think I've had any problems like these which are a  result of the type of file system.

---

### Post by subchief on 2011-06-19
> **nrundy said:**
> Read this to find out the differences:  [http://www.pcworld.com/businesscenter/article/230527/ubuntu_linux_day_16_ext4_vs_ntfs.html](http://www.pcworld.com/businesscenter/article/230527/ubuntu_linux_day_16_ext4_vs_ntfs.html)


In real world usage the big thing you will notice when comparing NTFS to Ext4 is that Ext4 will not deteriorate in performance with time. You can install and then use for several years with hardly any deterioration in performance.

With NTFS, you really should reformat and reinstall the OS about once a year because with continued use performance continues to decline. I've had Windows XP installs that moved at a snails pace after running for 3 years. A reformat and reinstall and it was snappy again for a little while.

Thanx...That article is an eye opener. And given the general direction of comments, i think it would be wise for me to format to ext4 format to avoid the possibility of being unable to repair the ntfs partition as i dont have a windows os installed!

---

### Post by nrundy on 2011-06-19
I would recommend you do a full install. That is, reinstall Ubuntu and during installation tell ubuntu to use the whole disk. Of course make sure you back up your /Home folder to CD/DVD before doing a complete reinstall.

---

### Post by jmore9 on 2011-06-19
I use 4 partitions with NTFS on them and 2 with EST4.  I only keep the NTFS so that the single windows machine can access the files, as it is easier for linux to use NTFS then windows to use EXT4.

Been doing this for about 2 years now.  If you do not have any windows machines that need to access the data on the NTFS parts then i would do one of the following :

copy the data from one partition at a time to another partition, then format the empty one to EXT4.  Then copy the data back if needed.  Do the same for all the rest.

If you can back up all the data on the NTFS partitions, ( to another drive which you can disconnect ) , then use geparted live cd and rearrange the partitions as you like - delete some - reformat the ones you keep to EXT4.

Or just keep on using them as they are.

---

### Post by subchief on 2011-06-19
> **nrundy said:**
> I would recommend you do a full install. That is, reinstall Ubuntu and during installation tell ubuntu to use the whole disk. Of course make sure you back up your /Home folder to CD/DVD before doing a complete reinstall.

Well...i wouldn't do that because i have music and movies saved on those partitions that i am not willing to let go of as yet. Would it cause any problem if i were to transfer the files to one partition and format the blank partition then move the files back without having to reinstall the OS?! i think that would be an unnecessary effort...

---

### Post by redmk2 on 2011-06-19
> **subchief said:**
> Well...i wouldn't do that because i have music and movies saved on those partitions that i am not willing to let go of as yet. Would it cause any problem if i were to transfer the files to one partition and format the blank partition then move the files back without having to reinstall the OS?! i think that would be an unnecessary effort...

When you format the partition the UUID will change and you will have to redo your /etc/fstab file.  This should not deter you from re-formating.  The benefits gained out weigh the trouble of the extra steps.

Speaking of the /etc/fstab file.  You can change the mount points when you re-format the partitions.  By this I mean a partition that is mounted at /mnt/media/ could be re-formated and the mount point changed to /music if you wanted.  You can design the file system as you want it.

---

### Post by subchief on 2011-06-20
> **redmk2 said:**
> When you format the partition the UUID will change and you will have to redo your /etc/fstab file.  This should not deter you from re-formating.  The benefits gained out way the trouble of the extra steps.

Speaking of the /etc/fstab file.  You can change the mount points when you re-format the partitions.  By this I mean a partition that is mounted at /mnt/media/ could be re-formated and the mount point changed to /music if you wanted.  You can design the file system as you want it.

Well,let me read more on the file system and then decide on what to do. Do you have any material that would help me make an informed decision in this regard?
Thank you!

---

### Post by redmk2 on 2011-06-20
> **subchief said:**
> Well,let me read more on the file system and then decide on what to do. Do you have any material that would help me make an informed decision in this regard?
Thank you!

Not really.  

I suggest you search Google for information on NTFS integration into Linux.  Ext2/3/4 file systems are Linux native file systems and are fully developed and understood in the FOSS world.  NTFS is a Microsoft file system and thus is closed source.  

Any integration of is best guess at what Windows is doing.  I doubt that Microsoft will let FOSS know of any updates or changes to the system.  This leaves you vulnerable as the translation can change at any time.

That alone should be enough for you to want to place your files on a file system supported by the OS you are using.  I have Vista and Win7 hosts.  They use NTFS and I trust that.  I have Linux hosts and I wouldn't think of using a non-native file system.

---

