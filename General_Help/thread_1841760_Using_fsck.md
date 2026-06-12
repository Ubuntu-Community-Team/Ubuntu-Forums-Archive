---
title: "Using fsck"
date: 2011-09-10
forum: General Help
---

### Post by alexis44 on 2011-09-10
I was looking thru the Disk Utility and saw that I had several errors or Bad Sectors.  I couldn't run the part where it checks for errors and repairs them, because my Hard Drive was Mounted.  I tried to UnMount it, but it said "The Device is Busy".  It also said I needed to be Root.  I tried the terminal, but I got the same answer.  Any advice?

---

### Post by lahirukannangara on 2011-09-10
> **alexis44 said:**
> I was looking thru the Disk Utility and saw that I had several errors or Bad Sectors.  I couldn't run the part where it checks for errors and repairs them, because my Hard Drive was Mounted.  I tried to UnMount it, but it said "The Device is Busy".  It also said I needed to be Root.  I tried the terminal, but I got the same answer.  Any advice?


Have you tried -f option on "sudo umount" command in terminal?

---

### Post by FormatSeize on 2011-09-10
> **alexis44 said:**
> I was looking thru the Disk Utility and saw that I had several errors or Bad Sectors.  I couldn't run the part where it checks for errors and repairs them, because my Hard Drive was Mounted.  I tried to UnMount it, but it said "The Device is Busy".  It also said I needed to be Root.  I tried the terminal, but I got the same answer.  Any advice?

What hardware do you have? Also, what disk utility are you using?

If you are trying to check for errors or bad sectors through some GUI of some sort, it probably won't work if you are using that disk to do what you are trying to do. In other words, if you need to check the disk for errors or bad sectors, you have to use something other than the file system that is on the disk you want to check; a Live CD or a utility like Hiren's Boot CD (or something like it). 

The reason why you can't unmount the disk (and this could be just a guess) is because you are using the disk to run the program that you want to check the disk with. But a little more detail on exactly what you are doing would clarify that.

---

### Post by fdrake on 2011-09-10
post here your ```
fdisk -lu
``` please.
you need to do fsck with a live cd/usb or through a separate linux partition or in grub.

---

### Post by Habitual on 2011-09-10
```
shutdown -rF now

```
or
```

sudo touch /forcefsck
``` and reboot.

---

### Post by alexis44 on 2011-09-10
1.  I Did try the -f option, and there was the same message.  

2.  I used the Live CD and still the same answer.  I haven't tried the -f option there.

3.  I tried using Grub through the Recovery Mode, but it didn't recognise any of the commands. 

4.  The command "sudo touch/forcefsck" , does that not force the system to start the fsck at boot?  Since I am assuming that the system is still mounted, will this not harm the file system?

---

### Post by oldfred on 2011-09-10
Must be unmounted:
Try "e2fsck -f /dev/sdb2". Ordinarily, fsck skips most of the check if the filesystem is marked as clean. The "-f" option to e2fsck (note: e2fsck, not fsck) forces a full check even if the filesystem is marked as clean.

#From liveCD so everything is unmounted,swap off if necessary, change sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems.
sudo e2fsck -C0 -p -f -v /dev/sdb1
#if errors:
sudo e2fsck -f -y -v /dev/sdb1

If still mounted issues:
Try this, is sure swapoff completed:
root@ubuntu# fuser -vam /dev/sda5
root@ubuntu# lsof /dev/sda5
Terminate with "kill [pid]" or "kill -9 [pid]

If above does not work:
Problem running e2fsck apparently in use by the system,  Use Slitaz
[http://ubuntuforums.org/showthread.php?t=1713946](http://ubuntuforums.org/showthread.php?t=1713946)
SATA will use sda1 and IDE devices use hda1 in Slitaz

---

### Post by oldos2er on 2011-09-10
> **alexis44 said:**
> 4.  The command "sudo touch/forcefsck" , does that not force the system to start the fsck at boot?  Since I am assuming that the system is still mounted, will this not harm the file system?

No, it's run early enough in the boot process that it won't harm anything. You left out a space in the command though, should be **sudo touch /forcefsck**

Just so you're aware though, bad sectors are usually not repairable. If the drive in question is still under warranty, you might look into getting it replaced.

---

