---
title: "How do I format HDD for use with Linux?"
date: 2010-08-16
forum: General Help
---

### Post by SNYP40A1 on 2010-08-16
I added an extra hard drive to my computer for backup purposes.  I had used it with a windows system and it was NTFS before I formatted it.  I used the recommended ext4 format.  However, I cannot access the disk.  It shows up on my desktop, but there's only one folder on it called lost+found and I cannot drop files into it.  What else do I need to do to use the drive?

---

### Post by deserthowler on 2010-08-16
Check permissions on the drive.  You might need to do chown and/or chmod to get it set up the way you want it.

Earl

---

### Post by deanjm1963 on 2010-08-16
when you formatted the drive did you give it a volume name?

I have a removable that I call "removable" when I format it.

Here is what I do.

Once I have formatted the drive I log out and log back in. The drive should now be mounted.

I open a terminal window and would do the following.

```
sudo chown -R dean:dean /media/removable
sudo chmod -R 755 /media/removable
sudo tune2fs -m 0 /dev/sdb1

```

you would need to change the "dean:dean" to your own log-in name, as well as where the drive is mounted - some drives might come up as /dev/sdc1

Hope this helps.

---

### Post by SNYP40A1 on 2010-08-21
Thanks for the advice.  My home computer is currently undergoing a hardware upgrade right now, but when I put it back together I'll try that.

---

### Post by Ginsu543 on 2010-08-22
Actually, if you're using this extra drive simply to store files, you can leave it formatted in NTFS. The Ubuntu OS has no problems whatsoever reading and writing to NTFS.

If you want to format the hard drive in something native to linux, you can format it to ext4, but in that case you must assign it a mount point.

---

### Post by SNYP40A1 on 2010-08-22
It's an external hard drive that I plan to use to backup a couple directories on one linux box.  So would ext4 be the best choice?

---

### Post by Ginsu543 on 2010-08-22
Ext4 should be fine for what you're trying to do.

---

### Post by SNYP40A1 on 2010-09-06
> **Ginsu543 said:**
> Ext4 should be fine for what you're trying to do.

It looks like it is formatted ext4, however, I cannot copy anything to the drive.  I want to use the drive as a backup drive.  When I click on the drive -> properties -> permissions, I see a message that states permissions cannot be determined.  Maybe that's part of the problem.

[[IMG]http://img824.imageshack.us/img824/9498/screenshotzi.th.png[/IMG]](http://img824.imageshack.us/i/screenshotzi.png/)

---

### Post by sandyd on 2010-09-06
> **SNYP40A1 said:**
> It looks like it is formatted ext4, however, I cannot copy anything to the drive.  I want to use the drive as a backup drive.  When I click on the drive -> properties -> permissions, I see a message that states permissions cannot be determined.  Maybe that's part of the problem.

[[IMG]http://img824.imageshack.us/img824/9498/screenshotzi.th.png[/IMG]]("http://img824.imageshack.us/i/screenshotzi.png/")
add "users" to the appropriate line in fstab, under the <opts> column

---

### Post by SNYP40A1 on 2010-09-06
> **carlee said:**
> add "users" to the appropriate line in fstab, under the <opts> column

Here's my fstab file:

> 
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=75c9f43c-1f90-465c-a591-299c8950f562 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=25c01217-25c0-49cb-8fe4-358be4c80488 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0


What am I supposed to change?  Can you edit it for me?  I don't want to mess up my system.

---

### Post by SNYP40A1 on 2010-09-08
[http://ubuntuforums.org/showthread.php?t=1220077](http://ubuntuforums.org/showthread.php?t=1220077)

---

