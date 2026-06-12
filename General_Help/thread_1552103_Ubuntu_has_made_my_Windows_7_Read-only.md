---
title: "Ubuntu has made my Windows 7 Read-only???"
date: 2010-08-13
forum: General Help
---

### Post by The1with2 on 2010-08-13
:confused:    :confused:    :confused:    :confused:
The title pretty much says it
i was on my laptop today using ubuntu, no duh.
i was accessing my windows 7 files without a problem to edit, add, or delete files.
then i turned it off because, well, just wanted to.
then i went back on it an hour later, logged in, and went to my windows 7 folder, only to relise i had to authenticate myself (which i never had to do before).
i went along and did it, but when i tried moving a folder it said :
"Error while copying to '(folder)'
The destination is Read-Only"
this happens with every folder i try in windows 7

i never had this problem and i have no idea what to do to remove read only.
please help me out.
:confused:    :confused:    :confused:    :confused:

---

### Post by Fafler on 2010-08-13
It's because the partition wasn't cleanly unmounted. The NTFS acts this way, because it has no way of knowing if the filesystem is bad and wants to protect the data against accidental overwrites. I don't know if theres a native tools to fix it, but apt-cache search fsck.ntfs doesnt give anything. Boot up windows to fix it and remember to unmount the partition cleanly ;-)

---

### Post by sikander3786 on 2010-08-13
I have been accessing Windows Drive from Ubuntu for a while and never had an issue. You might have messed up something by mistake.

Anyhow go to My Computer in Windows, right click the Drive on which you are having problems and go to Properties, then the Security Tab. Click on your user name and see what permission you've got. Adjust the permissions accordingly.

Post back if problems persist.

Regards.

---

### Post by lokojones on 2010-08-13
Post some info so we are able to help you out:

Run in the terminal (Alt+f2, then write "gnome-terminal" -without quotes- and press enter) the following:

```
cat /etc/fstab
```

And post the result here. Then to the same, but with the command:

```
mount
```

---

### Post by The1with2 on 2010-08-13
ok heres what i got : 
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=495dc550-36c3-468f-bf18-191e2469a62b /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=c765e53a-8f91-4698-b5c8-9c55ba78f0a4 none            swap    sw              0       0
 
not sure what that means
and for the second one i got this :

/dev/sda6 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)

hope that helps???
oh and my windows 7 doesnt boot which is why i am using Ubuntu

---

### Post by Fafler on 2010-08-13
Try accessing the partition and run mount again. It should tell you the devicename for the NTFS partition.

It turns out fsck.ntfs is called ntfsfix and included in the ntfsprogs package. Make sure it's installed with sudo apt-get install ntfsprogs an do a ntfsfix /dev/your-ntfs-partiton.

Edit: sudo fdisk -l is probably a better way than mount to figure it out. And make sure the partition is unmounted, otherwise ntfsfix probably won't run.

---

### Post by The1with2 on 2010-08-13
i tried the "ntfsfix /dev/your-ntfs-partiton" but got this :

"Failed to determine whether /dev/your-ntfs-partiton is mounted: No such file or directory.
Mounting volume... Error opening partition device: No such file or directory.
Failed to startup volume: No such file or directory.
FAILED
Attempting to correct errors... Error opening partition device: No such file or directory.
FAILED
Failed to startup volume: No such file or directory.
Volume is corrupt. You should run chkdsk."

then i tried "chkdsk" and got this :

/usr/bin/python: can't find '__main__.py' in '/usr/share/command-not-found'

do you know what this means??

Edit : just saw your edit, will try again

---

### Post by The1with2 on 2010-08-13
how do you unmount a partition??

---

### Post by The1with2 on 2010-08-13
ok, i did it again, unmounted and got this :

Mounting volume... Error opening partition device: Permission denied.
Failed to startup volume: Permission denied.
FAILED
Attempting to correct errors... Error opening partition device: Permission denied.
FAILED
Failed to startup volume: Permission denied.
Volume is corrupt. You should run chkdsk.

i tried chkdsk again but it still failed??? 
im stumped on what to do

---

### Post by philinux on 2010-08-13
> **The1with2 said:**
> i tried the "ntfsfix /dev/**your-ntfs-partition**" but got this :

"Failed to determine whether /dev/**your-ntfs-partition** is mounted: No such file or directory.


your-ntfs-partition = sda1 or sdb1 or sdc etc etc etc.

---

### Post by The1with2 on 2010-08-13
oh lol, thanks philinux.
this is what i got now :

jacob@jacob-laptop:~$ ntfsfix /dev/sda1
Refusing to operate on read-write mounted device /dev/sda1.
jacob@jacob-laptop:~$ ntfsfix /dev/sda1
Mounting volume... Error opening partition device: Permission denied.
Failed to startup volume: Permission denied.
FAILED
Attempting to correct errors... Error opening partition device: Permission denied.
FAILED
Failed to startup volume: Permission denied.
Volume is corrupt. You should run chkdsk.

still not good =[

---

### Post by Mark Phelps on 2010-08-13
Contrary to popular opinion, ntfsfix can not fix ALL NTFS problems, only some of them.

You will need to run chkdsk from an MS Windows boot in order to TRY to fix the NTFS volume.

Since you probably did NOT use the Win7 Backup feature to create and burn a Win7 Repair CD (which would come in real handy about now), go to the link below, download and burn a Win7 Repair CD;

[http://neosmart.net/blog/2009/windows-7-system-repair-discs/]("http://neosmart.net/blog/2009/windows-7-system-repair-discs/")

Once you have that, boot into a command line using that CD and run chkdsk from there.

Good luck.

---

### Post by lokojones on 2010-08-17
> **The1with2 said:**
> oh lol, thanks philinux.
this is what i got now :

jacob@jacob-laptop:~$ ntfsfix /dev/sda1
Refusing to operate on read-write mounted device /dev/sda1.
jacob@jacob-laptop:~$ ntfsfix /dev/sda1
Mounting volume... Error opening partition device: Permission denied.
Failed to startup volume: Permission denied.
FAILED
Attempting to correct errors... Error opening partition device: Permission denied.
FAILED
Failed to startup volume: Permission denied.
Volume is corrupt. You should run chkdsk.

still not good =[

You need permission's to run ntfsfix.
Just type: ```
sudo ntfsfix /dev/sda1
```
Good luck.

---

