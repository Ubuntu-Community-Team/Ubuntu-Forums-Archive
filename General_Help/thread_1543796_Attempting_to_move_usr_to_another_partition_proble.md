---
title: "Attempting to move /usr to another partition problem"
date: 2010-08-01
forum: General Help
---

### Post by CyberAxe on 2010-08-01
I recently bought a SSD and decided to give the majority of the space to windows for production purposes I gave 3.5GB for ubuntu but that filled up rather fast so i decided to move the folder taking up the most space to another partition which is /usr.

I tried moving the /usr to another partition and using a symbolic link but that didn't work so i'm trying (and would prefere this method anyway) to use fstab to do it

```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system>				  <mount point>   	       <type>  <options>       	  <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=6235f221-8cec-4a00-b5c0-afbe07cb308f /               		ext4    errors=remount-ro 0       1

# /storage/
UUID=6b5496b1-99ab-4a12-ba38-0caf57be8ad6 /media/Storage	  	ext4	errors=remount-ro 0     

UUID=9C3A5D753A5D4E00 			  /media/Document\040Storage	ntfs    defaults,nls=utf8,umask=007,gid=46 0       0
UUID=CC4A8AF34A8ADA1A			  /media/Entertainment		ntfs    defaults,nls=utf8,umask=007,gid=46 0       0
UUID=DC5E5E0A5E5DDE38 			  /media/Game\040Storage	ntfs    defaults,nls=utf8,umask=007,gid=46 0       0

/usr					  /media/Storage/usr		ext4	rw,bind 	  0	  0
/var/tmp				  /media/Storage/var/tmp	ext4	rw,bind 	  0	  0
/var/cache/apt				  /media/Storage/var/cache/apt	ext4 	rw,bind 	  0	  0
/var/cache/tmp				  /media/Storage/var/cache/tmp	ext4 	rw,bind 	  0	  0

# swap was on /dev/sda6 during installation
UUID=3269483f-f427-4230-929f-608414d17f89 none		          	swap    sw           	  0       0
# swap was on /dev/sde3 during installation
UUID=98c8e337-b553-4478-b8b2-804bf00af539 none 		          	swap    sw                0       0

```

The code above should in theory work form what i have been able to find on google, however there is obviously something wrong with it, anyone have any ideas? thanks.

---

### Post by limestone on 2010-08-01
I don't think you can move the /usr folder.. what you can do is create a symbolic link on your SSD that point to /usr.
If you need more space, install Ubuntu on a bigger disk or use your SSD for music and other stuff instead of the primary.

---

### Post by The Cog on 2010-08-01
Coincidentally, I read a post yesterday from someone moaning about the state of Ubuntu bugs. He said he had filed a bug report a while ago that he felt should be given more attention. I didn't follow the details, but I got the impression that mountall as used in Lucid cannot cope with /usr being on a separate partition. I gather it is addressed in Maverick but not back-ported to Lucid.

Ah, found it: [http://ubuntuforums.org/showthread.php?t=1542285](http://ubuntuforums.org/showthread.php?t=1542285)

---

### Post by CyberAxe on 2010-08-01
Right after posting I was looking at the fstab stuff and realised the folders were the wrong way round compared to the drive mounts ie location then mountpoint, where as the folders were mountpount then location I switched them round and it worked.

Thanks for the replies.

> 
If you need more space, install Ubuntu on a bigger disk or use your SSD for music and other stuff instead of the primary.

Using a SSD for music and data rather than the OS seems rather a waste (considering Ubuntu loads almost instantaneously as opposed to around the 5-10 seconds of the newer versions) Windows 7 and XP are down to 10 seconds and 3 seconds respectively, which you have to admit is impressive (besides 3.5GB certainly aint enough to store my music collection on ;)).

---

