---
title: "Symlink unavailable without touching target with file manager"
date: 2011-04-22
forum: General Help
---

### Post by jimberry on 2011-04-22
I have a dual-boot setup with Ubuntu and Windows 7, sharing an NTFS file system.

If I create a new folder (called "newfolder") in the root of my Windows 7 partition, with a text file called newtextfile.txt, and then create a symlink in Ubuntu with

ln -s /media/S3A8115D003/newfolder

I can then see, read and edit "newtextfile.txt" from Ubuntu, until I log out and reboot.
After I reboot, the symlink to newfolder still appears to be there but when I try to access it, I get *This link cannot be used, because its target "media/S3A8115D003/newfolder" doesn't exist.*
However, if I first navigate in the file manager to the Windows folder S3A8115D003/newfolder and view its contents, then the Ubuntu symlink appears to be healed. 

How can I make the symlink work without first having to touch the target file with the file manager?

---

### Post by Dave_L on 2011-04-22
You probably need to mount /media/S3A8115D003 automatically,  by adding it to /etc/fstab.

You can determine what's currently mounted using the command "mount" or the command "df -hT".

---

### Post by jimberry on 2011-04-22
The last line displayed from "df -hT" is
/dev/sda2  fuseblk    253G  165G   88G  66% /media/S3A8115D003

---

### Post by jimberry on 2011-04-22
Sorry, I should have rebooted before that, of course.
Now, having rebooted,  /dev/sda2 fuseblk 253G 165G 88G 66% /media/S3A8115D003 does not show up

---

### Post by Dave_L on 2011-04-22
That confirms that mounting the device is what's needed.

Look at the line for that device in the output from the "mount" command, or in the file /etc/mtab.

Then use that as a guideline for adding a line to /etc/fstab to automatically mount the device.

I haven't done that type of thing for a while, and can't tell you exactly how to do it, but maybe someone else can provide more specifics.

---

### Post by jerome1232 on 2011-04-22
here is a [Guide to Fstab]("http://ubuntuforums.org/showthread.php?t=283131")

---

### Post by jimberry on 2011-04-22
From jerome1232's "Guide to fstab" link
[I]Options for mount and fstab are similar.
[/I]
Does  this mean that I can just add to fstab this line as output from mount -l 
*/dev/sda2 /media/S3A8115D003 fuseblk rw,nosuid,nodev,allow_other,blksize=4096,default_permissions 0 0*
to have the partiton mounted at boot?
====
Obviously not - when i tried that, I got the message "An error occurred while mounting /media/S3A8115D003"

---

### Post by oldfred on 2011-04-23
A few more links. I do not recommend mounting the windows system partition read/write. Windows often is not happy after you start doing a lot of writes into its system. Also Ubuntu does not hide the system files so it is easy to accidentally damage the system. It is much better to create another shared NTFS partition.

Understanding fstab
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)
[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

Ownership and permissions of vfat / ntfs are set at the time of mounting. This is often a source of confusion.
[http://www.psychocats.net/ubuntu/mountwindowsfstab](http://www.psychocats.net/ubuntu/mountwindowsfstab)
HOWTO: Mount NTFS partitions with specific ownership/permissions 
[http://ubuntuforums.org/showthread.php?t=1604251](http://ubuntuforums.org/showthread.php?t=1604251)

I mount my NTFS as /mnt so it does not show in Nautilus, but then link back the folders from shared I want to use.

mkdir /mnt/shared
Edit fstab but use your UUIDs from this:
sudo blkid

# modify fstab to mount directory
gksudo gedit /etc/fstab

```
# Entry for /dev/sdc2 :
UUID=44332FD360AA9657                      /mnt/shared  ntfs-3g      defaults                             0  0  

```

# remount from updated fstab before rebooting - if no errors it has remounted
sudo mount -a

---

### Post by jimberry on 2011-04-23
Thanks for your help, guys, I think I have now been able to  achieve what I needed to do.

I think I have been able to get around the Windows problem (mentioned by oldfred) by moving the required folder from Users/Jim/AppData/Roaming/Jalbum in the C: systems partition to my E: Data partition and replacing it in the original location with a Windows "junction" link.
*mklink /j skins E:\Data\jAlbumSkins*

After checking that the Windows app could still access the data via the "junction", I changed the Ubuntu symlink to also point to the new location on E:\Data\jAlbumSkins
*ln -s /media/Data/jAlbumSkins*

and added the E: partition to the Ubuntu file system table to be mounted at boot time.

This now allows me to create an album using jAlbum on Ubuntu with the skins installed for Windows in E:\Data\jAlbumSkins

I will give it a more thorough test tomorrow.

---

