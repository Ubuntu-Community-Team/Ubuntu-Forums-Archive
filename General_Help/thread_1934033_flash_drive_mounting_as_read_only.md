---
title: "flash drive mounting as read only"
date: 2012-03-01
forum: General Help
---

### Post by SirThom on 2012-03-01
Hi!  I have a Kensington Flash Drive that I bought a month ago, formatted as NTFS, and have been using happily since then.  Suddenly I'm discovering that Ubuntu treats it as Read-Only.  Can anyone possibly help me to puzzle this out?
Here are the listings of mount and cat /etc/fstab.  The drive is called sprite.  I use it in both Windows and Ubuntu, but mainly Ubuntu.  I am running Ubuntu 11.10.

[FONT="Trebuchet MS"]thodges@Ptolemy:~$ mount
/dev/sda5 on / type ext4 (rw,errors=remount-ro,commit=0)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/thodges/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=thodges)
/dev/sda1 on /media/Ptolemy type ntfs (ro,nosuid,nodev,uid=1000,gid=1000,dmask=0077,fmask=0177,uhelper=udisks)
/dev/sdb1 on /media/sprite type ntfs (ro,nosuid,nodev,uid=1000,gid=1000,dmask=0077,fmask=0177,uhelper=udisks)



thodges@Ptolemy:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=58e90287-322d-4424-9100-6691110be85b /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=be3cc07d-ba68-4028-a8ce-98dfbb46199f none            swap    sw              0       0
[/FONT]

---

### Post by dino99 on 2012-03-01
use chmod

[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

---

### Post by egalvan on 2012-03-01
One reason Linux mounts Microsoft NTFS as read-only is because the volume was not un-mounted cleanly the last time Windows mounted it... the "dirty-bit" is set and Linux (wisely) refuses to write to it, as this can cause data corruption...

A possible fix...
Mount it on a Windows machine, then **BE SURE** to use the "safely disconnect hardware" icon ...

you may want to run "check disk for errors" from Windows also....

---

### Post by imachavel on 2012-03-01
> **dino99 said:**
> use chmod

[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

chmod
chmod: missing operand
Try `chmod --help' for more information.

I'm a little unfamiliar with the linux file system directories. I'm still a little newbish. in windows the pen drive would show up as a letter (f: for example) in my computer, but then there is really no way to open files in windows, cd d: just says

the device is not ready

I'm sorry to ask such a retarded newbish question. to chmod into my flash drive I'd need to know what directory to cd to correct? Now chmod will do what exactly? I have files on my flash drive, I also have an installed partition and OS on the flash drive, there are folders for boot and grub. I can't boot to the usb device though. I suppose that could just be old mobo old bios doesn't like the idea of booting to a flash drive. To OP yes eject safely or files will be corrupted, and then the OS will only see file addresses and will say it's 'read only', meaning only the names of the files exist basically. ntfs flash drives wipe files ALL the time. sorry to say. Otherwise I'd say it's a permission issue, but then why need permissions to open a drive that is loaded on a mounted file system, unless you encrypted the drive, after all you aren't accessing files from one mounted file system to another. to mount the drive you sit on top of it's file system, so to access files is the drive mounted? Or is the drive only mounted when an OS is loaded?

Here is my 


cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=4b94c53e-8dc8-45b9-af1e-aa6f47568e1e /               ext3    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=f429ac74-87eb-40e9-a0cc-7ecceb923edc none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0



sorry to hijack the thread, but I've started too many threads on this subject that never get answered. I thought it wouldn't hurt to ask in this thread :popcorn:

---

### Post by imachavel on 2012-03-01
good idea, when you pop the flash drive into windows, note the drive letter, let's say for example it's f:

then open command line, and type

chkdsk /f :f

or chkdsk /r :f

can you not fsck a drive in linux? I'm surprised you mentioned to chkdsk in windows and not how to chkdsk in linux

FOR MY PREVIOUS QUESTION, A THE FLASH DRIVE IS MOUNTED WHEN YOU CAN SEE IT'S FILES. TO RUN CHKDSK ON MY FLASH DRIVE IN WINDOWS I FIRST MUST DISMOUNT THE VOLUME

---

### Post by SirThom on 2012-03-01
> **dino99 said:**
> use chmod

[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

I tried not chmod, but doing the equivalent through right clicking in GNOME and selecting Properties.  It just old me that the disk was read only when I tried to make changes to make it read and write.

---

### Post by SirThom on 2012-03-01
> **imachavel said:**
> good idea, when you pop the flash drive into windows, note the drive letter, let's say for example it's f:

then open command line, and type

chkdsk /f :f

or chkdsk /r :f

can you not fsck a drive in linux? I'm surprised you mentioned to chkdsk in windows and not how to chkdsk in linux

FOR MY PREVIOUS QUESTION, A THE FLASH DRIVE IS MOUNTED WHEN YOU CAN SEE IT'S FILES. TO RUN CHKDSK ON MY FLASH DRIVE IN WINDOWS I FIRST MUST DISMOUNT THE VOLUME

I can try that.  I *did* recently open it in XP to see if it needed fixing, and even used ccleaner to defrag it in case that might fix it.  No chkdsk though...

---

### Post by imachavel on 2012-03-01
c cleaner won't defrag it. chkdsk will defrag it. c cleaner cleans out un used or incorrect registry values. While you are at it run a virus scan on it as well. If you can't get your files back then sorry. Sometimes things happen, what can you do??

---

### Post by SirThom on 2012-03-01
> **imachavel said:**
> c cleaner won't defrag it. chkdsk will defrag it. c cleaner cleans out un used or incorrect registry values. While you are at it run a virus scan on it as well. If you can't get your files back then sorry. Sometimes things happen, what can you do??

I'm not worried about getting my files back.  I can access the flash drive easily in XP, I just want to be able to use it in Ubuntu.  Actually it wasn't Ccleaner I used to defrag but some other disk maintenance software, can't remember the name.  It certainly defragged because I saw the disk map as it did that both to my HD and my flash drive.

I actually did try chkdsk.  It *did* fix something with the file system, but Ubuntu still isn't accepting it...

---

### Post by SirThom on 2012-03-02
update:
I've fixed the drive in Windows a few times and also formatted it in Ubuntu several times.  It still shows up as a read-only system.

---

### Post by SirThom on 2012-03-02
I just solved it by installing ntfs-config and enabling writing to external ntfs devices.  I'm not sure why it worked before and stopped working, but it's working now.

---

