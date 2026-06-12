---
title: "Mounting local filesystems &quot;fails&quot; during boot, but everything appears fine."
date: 2006-05-11
forum: General Help
---

### Post by KillrBuckeye on 2006-05-11
Hello, I am very new to Linux, and having just resolved my first major issue (related to nVidia drivers), it's on to the next one! :)  This failure to mount local filesystems was originally a result of deleting and recreating my /home and swap space partitions.  However, some friends helped me to remount these partitions using fdisk, mount, and umount commands along with modifications to the fstab file.  Now when I boot up, I see everything of importance, including my /home, swap space, NTFS Windows partitions and my FAT32 partition for shared storage, and they all appear to be moutned correctly.  I don't understand why the "Mounting Local Filesystems" status is being reported as [FAIL].

Is there a detailed log of the boot process that is automatically created somewhere?  If so, would this log contain more descriptive errors that could point me to the device that failed to mount?  Any suggestions would be appreciated! :)

---

### Post by Sef on 2006-05-11
I had the same problem once.  Eventually I had to reinstall my os.  Not sure if you will have to, but you may.

---

### Post by Irony on 2006-05-11
Your */etc/fstab* file has an entry to a non-existent folder hence it fails to load it. See that this file matches your partition table;

[PHP]sudo fdisk -l[/PHP]

---

### Post by Dogmeat on 2006-05-11
On fstab, try adding the "noauto" option to devices that you don't want ubuntu to automatically mount on boot (such as cd-roms, floppy disks, usb sticks) as the media may not be in the drive, and you will see the failed message.

However don't worry about having to mount cd-roms manually every reboot, as pmount will automatically mount a cd-rom if it is detected, even if you set the "noauto" option!

---

### Post by AndrewCaul on 2006-05-11
Press Alt-F1 when booting up to see the bootup process in more detail. It should tell you why it's failing.

---

### Post by KillrBuckeye on 2006-05-11
Wow!  Four replies in 20 minutes, you guys are great.  I will first compare my fstab file to my partition table.  If that checks out, I will add the "noauto" option to my removable devices.  I'll let you know how it goes when I get home from work.  Thanks for your help!

---

### Post by KillrBuckeye on 2006-05-11
Hey guys thanks for your help!  I discovered that there was a problem mounting one of my NTFS partitions (I think my partition table might be screwed up).  Anyhow, removing this from the fstab file fixed the problem with Ubuntu reporting a failure to mount local filesystem.

However, now I have another strange problem.  My networking/internet is messed up, and it was working just fine an hour ago:
[http://ubuntuforums.org/showthread.php?p=1007038#post1007038]("http://ubuntuforums.org/showthread.php?p=1007038#post1007038")

---

