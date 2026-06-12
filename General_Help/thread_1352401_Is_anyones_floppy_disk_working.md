---
title: "Is anyones floppy disk working?"
date: 2009-12-11
forum: General Help
---

### Post by AKADAP on 2009-12-11
Please stick a floppy disk in your drive and see if you can read it.

I have two machines running 9.10, neither can recognize media in the floppy drives, both were working before 9.10.

I have heard reports of two others who have the same problem.

I have heard no reports of a working floppy drive under 9.10, but I don't think my previous thread on the matter got enough exposure for me to claim that there are no working floppies on 9.10

I have some old test equipment for which the only means of transferring data is floppy disk. It would be nice if I could still use it.

---

### Post by ron999 on 2009-12-11
**Is anyones floppy disk working?**

Yes, do this.
Insert the floppydisk into the drive then enter in a monitor:-
```
sudo mount /dev/fd0
```
Then you will see the floppy listed under 'Places'.
And you can access it.
If I want to write to a mounted floppydisk I open it using:-
```
sudo nautilus
```
When you've finished you can unmount it using:-
```
sudo umount /dev/fd0
```
:)

Also this guy here explains how to format a 1.4MB floppy:-
[http://ubuntuforums.org/showthread.php?p=8452939#post8452939]("http://ubuntuforums.org/showthread.php?p=8452939#post8452939")
The command is:-
```
sudo mformat -f 1440 A:
```
:)

---

### Post by AKADAP on 2009-12-12
> **ron999 said:**
> **Is anyones floppy disk working?**

Yes, do this.
Insert the floppydisk into the drive then enter in a monitor:-
```
sudo mount /dev/fd0
```
Then you will see the floppy listed under 'Places'.
And you can access it.
If I want to write to a mounted floppydisk I open it using:-
```
sudo nautilus
```
When you've finished you can unmount it using:-
```
sudo umount /dev/fd0
```
:)

Also this guy here explains how to format a 1.4MB floppy:-
[http://ubuntuforums.org/showthread.php?p=8452939#post8452939]("http://ubuntuforums.org/showthread.php?p=8452939#post8452939")
The command is:-
```
sudo mformat -f 1440 A:
```
:)

No joy:

```
user@computer:~$ sudo mount /dev/fd0
[sudo] password for user: 
mount: can't find /dev/fd0 in /etc/fstab or /etc/mtab
user@computer:~$

```

But unlike nautilus, this gives a clue as to what might be wrong. 
Of course I have no clue as to what should be in those files that isn't.
/etc/fstab:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=b5a554b5-92df-4492-abbf-290fd809d2c0 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=6c05a1b6-6f07-4b71-b070-2275796b41c0 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

```
/etc/mtab:
```
/dev/sda1 / ext3 rw,relatime,errors=remount-ro 0 0
proc /proc proc rw 0 0
none /sys sysfs rw,noexec,nosuid,nodev 0 0
none /sys/fs/fuse/connections fusectl rw 0 0
none /sys/kernel/debug debugfs rw 0 0
none /sys/kernel/security securityfs rw 0 0
udev /dev tmpfs rw,mode=0755 0 0
none /dev/pts devpts rw,noexec,nosuid,gid=5,mode=0620 0 0
none /dev/shm tmpfs rw,nosuid,nodev 0 0
none /var/run tmpfs rw,nosuid,mode=0755 0 0
none /var/lock tmpfs rw,noexec,nosuid,nodev 0 0
none /lib/init/rw tmpfs rw,nosuid,mode=0755 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
gvfs-fuse-daemon /home/user/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user=user 0 0

```

I find it odd that USB drives show up & mount just fine, but the floppy disk does not. I do not see anything about the USB drives in these files either.

---

### Post by emigrant on 2009-12-12
floppy drive on in bios?

---

### Post by Shazaam on 2009-12-12
If it is on in your bios (and connected) add this to your /etc/fstab...
```
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
```

EDIT: Arggh! The same (or similar) thing as Intrepid! The only way for me to mount a floppy in Karmic is with root. Did a sudo modprobe floppy which only resulted in the floppy light flashing. Time to dig.

---

### Post by lisati on 2009-12-12
No problems here with a USB floppy drive in 9.04..... maybe this thread is something to be aware of if and when I upgrade?

---

### Post by ron999 on 2009-12-12
@ AKADAP
As Shazaam said above, an extra line needs adding to your /etc/fstab.
Here is mine:-
```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=208dd644-1221-4cc2-b88f-1dc6595095a5 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=cba2ada5-dbb8-4216-934b-6bfaa2c3b1df none            swap    sw              0       0

/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
```

Also there is no mention of fd0 in my /etc/mtab file either, so don't worry about that.
:D

---

### Post by ron999 on 2009-12-12
> **Shazaam said:**
> 

EDIT: Arggh! The same (or similar) thing as Intrepid! The only way for me to mount a floppy in Karmic is with root. Did a sudo modprobe floppy which only resulted in the floppy light flashing. Time to dig.

Yes, I had this problem with Dapper Drake, then it was fixed with Feisty Fawn and now it's back again with Karmic Koala.

:confused:

---

### Post by Shazaam on 2009-12-12
ron999 and others...
Yes I have that line in fstab but as I just discovered my floppy will NOT mount as a normal user through Places>Floppy or /media/floppy0 with nautilus. I opened nautilus as root-
```
gksudo nautilus
```
and the floppy mounts. Subsequently I added myself to disk and floppy in Users and Groups with no change (even after a reboot). A bug report has already been filed-
[https://bugs.launchpad.net/ubuntu/+source/devicekit-disks/+bug/441835](https://bugs.launchpad.net/ubuntu/+source/devicekit-disks/+bug/441835)

Here are three temporary workarounds...
A. DANGEROUS! Open nautilus as root as stated before.
B. In terminal, cd to /media/floppy and enter-
<snip-doesn't work>
C. Again in terminal-
```
devkit-disks --mount /dev/fd0
```

---

### Post by ron999 on 2009-12-12
OK Shazaam we will have to live dangerously till those guys at bugs.launchpad.net get it sorted out.
:lolflag:

---

### Post by sar59 on 2009-12-29
Using command sudo mount /dev/fd0 in karmic I get this...                                                                     mount: wrong fs type, bad option, bad superblock on /dev/fd0,        missing codepage or helper program, or other error        In some cases useful info is found in syslog - try        dmesg | tail  or so                                                                           The same setup works fine in windows... :(

---

### Post by cebif on 2010-01-24
> **Shazaam said:**
> ron999 and others...
Yes I have that line in fstab but as I just discovered my floppy will NOT mount as a normal user through Places>Floppy or /media/floppy0 with nautilus. I opened nautilus as root-
```
gksudo nautilus
```
and the floppy mounts. Subsequently I added myself to disk and floppy in Users and Groups with no change (even after a reboot). A bug report has already been filed-
[https://bugs.launchpad.net/ubuntu/+source/devicekit-disks/+bug/441835](https://bugs.launchpad.net/ubuntu/+source/devicekit-disks/+bug/441835)

Here are three temporary workarounds...
A. DANGEROUS! Open nautilus as root as stated before.
B. In terminal, cd to /media/floppy and enter-
<snip-doesn't work>
C. Again in terminal-
```
devkit-disks --mount /dev/fd0
```
I have the same problem to in Ubuntu 9.10.
I tried first the commands A & C and they worked. I then added the line:
```
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
``` as
in post before because it was not in fstab, now none of the commands work.
It returned this error:
```
$ devkit-disks --mount /dev/fd0
Mount failed: Error mounting: mount exited with exit code 1: helper failed with:
mount: mount point /media/floppy0 does not exist

```
So I will remove it.
It is a real frustration if the bug has been in other versions and keeps returning, especially if it returns for long periods.

---

### Post by plucky on 2010-01-25
> **cebif said:**
> I have the same problem to in Ubuntu 9.10.
I tried first the commands A & C and they worked. I then added the line:
```
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
``` as
in post before because it was not in fstab, now none of the commands work.
It returned this error:
```
$ devkit-disks --mount /dev/fd0
Mount failed: Error mounting: mount exited with exit code 1: helper failed with:
mount: mount point /media/floppy0 does not exist

```
So I will remove it.
It is a real frustration if the bug has been in other versions and keeps returning, especially if it returns for long periods.

Try ```
sudo mkdir /media/floppy0
```

Put a floppy in and ```
mount /dev/fd0
```

For some reason it will not mount using the icon in Places.

Good luck

---

### Post by cebif on 2010-01-25
> **plucky said:**
> Try ```
sudo mkdir /media/floppy0
```

Put a floppy in and ```
mount /dev/fd0
```

For some reason it will not mount using the icon in Places.

Good luck
Thanks, that worked. Without the line in fstab```
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
```
line I was able to use:```
$ devkit-disks --mount /dev/fd0
``` to mount and open floppy disks but not write to them or delete anything.
With the line back in fstab and trying your commands I can now do both.

---

