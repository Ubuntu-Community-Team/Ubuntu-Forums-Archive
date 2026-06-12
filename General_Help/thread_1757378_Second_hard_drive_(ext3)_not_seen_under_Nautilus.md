---
title: "Second hard drive (ext3) not seen under Nautilus"
date: 2011-05-13
forum: General Help
---

### Post by Eromatic on 2011-05-13
Under Ubuntu 11.04, Nautilus isn't seeing my second hard drive (ext3 200GB). ...It's a backup of my home folder that was on the Ubuntu 8.04 primary drive. So how does one go about copying the data from the second hard drive to the primary hard drive then? I'm kind of dead in the water at this point.


[[IMG]http://img853.imageshack.us/img853/9895/mounterror1104.th.png[/IMG]](http://img853.imageshack.us/i/mounterror1104.png/)

---

### Post by oldfred on 2011-05-13
Disk Utiliy is showing not mount, but your error is that it is mount. Did you click on an entry in the left panel of Nautilus that says 200GB after showing the disk utility screen?

It is best to mount and set ownership & permissions. If you are regularly going to use it, you should add it to fstab.

sudo umount /dev/sdb1
sudo mkdir /data
sudo mount /dev/sdb1 /data
#where sdb1 needs to be your drive, partition
#if not known to list partitions
sudo fdisk -l

#If you cannot read and write then change the permissions. Not for NTFS
# Note that the -R is recursion and everything is changed, do NOT run on non data partitions.
$ sudo chmod -R 777 /data
sudo chown -R fred:fred /data
#where fred should be your login name
#or
echo $USER
sudo chown -R $USER:$USER /data

Understanding fstab
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
Above link was this post before:
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)
[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

Edit - change mount
Above example mounts /data in /, so you have to search to find in from / (root)
May be better to mount in /mnt/data or /home/data

---

### Post by Eromatic on 2011-05-13
The 200GB had never once appeared at left panel of Nautilus under 11.04. ...The 200GB is just temporary until its contents can be transferred to the primary hard drive (Ext4 251GB).


**Edit:**

Disk Utility info on the primary hard drive. (Ubuntu 11.04)
[[IMG]http://img845.imageshack.us/img845/2118/mounterror21104.th.png[/IMG]](http://img845.imageshack.us/i/mounterror21104.png/)

---

### Post by Eromatic on 2011-05-13
Getting a error at step 1. I tried rebooting, but I keep seeing the following:


sudo umount /dev/sdb1

umount: /: device is busy.
        (In some cases useful info about processes that use
         the device is found by lsof(8) or fuser(1))


**Edit:**

At one point System Monitor indicates that the primary hard drive is mounted to /dev/sdb1   (Directory /), and now after a few reboots, System Monitor indicates that the primary hard drive is mounted to /dev/sda1 ..!

[[IMG]http://img39.imageshack.us/img39/8869/mounterror41104.th.png[/IMG]](http://img39.imageshack.us/i/mounterror41104.png/)

So step one is a go at the moment...


**Edit2:**

Success!

[[IMG]http://img685.imageshack.us/img685/2840/mounterror51104.th.png[/IMG]](http://img685.imageshack.us/i/mounterror51104.png/)

After doing command (*sudo umount /dev/sdb1*), I went to the Disk Utility and clicked on the Mount Volume button for the 200GB Hard Disk, where it then mounted successfully. I suspect that the 200GB will not be there upon reboot though. ...The 200GB drive will be remove anyway after the copy process is done.

Thank you for your help and time.

---

### Post by oldfred on 2011-05-13
I have seen the busy on partitions that needed fsck and would not unmount to run fsck in Ubuntu. The work around was to download and boot another install and run it from there:

From liveCD so everything is unmounted,swap off if necessary, change sdb1 to your partition(s)
e2fsck is used to check the ext2/ext3/ext4 family of file systems.
sudo e2fsck -C0 -p -f -v /dev/sdb1
if errors:
sudo e2fsck -f -y -v /dev/sdb1

Since it is sdb1 and not part of your working system you can try this also, may need sudo from working system:
Try this, is sure swapoff completed (not required if not liveCD):
root@ubuntu# fuser -vam /dev/sdb1
root@ubuntu# lsof /dev/sdb1
Terminate with "kill [pid]" or "kill -9 [pid]
If not:
Problem running e2fsck apparently in use by the system,  Use Slitaz
[http://ubuntuforums.org/showthread.php?t=1713946](http://ubuntuforums.org/showthread.php?t=1713946)
SATA will use sda1 and IDE devices use hda1 in Slitaz

---

