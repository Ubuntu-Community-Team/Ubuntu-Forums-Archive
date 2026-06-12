---
title: "RAID1 array won't mount in 10.10"
date: 2010-10-03
forum: General Help
---

### Post by blairnic on 2010-10-03
I am having a RAID problem and would appreciate any suggestions. I searched the forums but don't see this exact problem.  Everything worked under Ubuntu 9.04 and am now testing Ubuntu 10.10 and having a problem. 
 
I have 3 drives: a 100GB primary drive for the OS and home and 2 1-TB drives that are purely for data. I am able to RAID1 the pair of TB drives just fine using mdadm and the md0 array status appears to be fine.  I believe the next step is to mount the array.    I created a mount point: mkdir /media/array with no problem. 
 
When I mount the array with sudo mount /dev/md0 /media/array, I get a standard, generic mount error listing 20 possible reasons mount failed: "wrong fs type, bad option, bad superblock on md0....  I tried re-running mount with a specified file type and same result. I tried a few different file system types with same result. Running dmesg | tail as suggested indicates the files system can't be found.
 
Question: Do I have to specify an md0 filesystem when running the mount command or should the OS be able to figure it out automatically?  
 
Question: How do I determine what filesystem to use for md0?  Does the md0 filesystem have to be identical to my /dev/sdg and /dev/sdh hard drive filesystems?
 
Question:  How can I determine/verify the underlying /dev/sdg and /dev/sdh filesystems? I don't remember for sure what they are (I'm pretty sure they are ext3 or vfat as this was a samba share under 9.04).  I have not found how to do this with mdadm and most standard diagnostic tools, including the boot_info_script shell script do not report many physical drive details once the drive is in an array. 
 
This thread:
 
[http://ubuntuforums.org/showthread.php?t=1513405](http://ubuntuforums.org/showthread.php?t=1513405)
 
implied I need to define a filesystem for md0 using this command: 
 
mke2fs -t ext3 /dev/md0
 
but I am frankly terrified that this command will wipe or render unreadable critical data already sitting on the 1 TB drives. I'm trying to mount these without trashing the data already on the drives.  Is it safe to run this command?
 
The same thread talked about updating mdadm.conf, but I would like to be able to do this manually and be comfortable with it, because using mdadm.conf to automate anything. 
 
Any assistance appreciated as I'm struggling a bit and concerned about losing my data. 
 
Thanks.

---

### Post by at165db on 2010-10-12
Running 
mke2fs -t ext3 /dev/md0
will format the raid array, so you'd loose data on those drives contained in that raid device.

I don't know the specifics as I'm a bit rusty with command line mount, but I know that you can mount a drive belonging to a softraid 1 array by its self, even if you cannot boot off the drive.  (it should still have /dev/sd#a /dev/sd#b etc.) and those partitions would be the underlying format of what your softraid 1 array was.

---

