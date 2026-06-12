---
title: "Unrecognized mount option &quot;errors=remount-rw&quot; or missing value"
date: 2010-11-04
forum: General Help
---

### Post by eawim on 2010-11-04
Hi,
made an upgrade to version 10.10 - after that following error occured:

fsck from util-linux-ng 2.16
Adding 63857963k swap on /dev/sda5/
EXT3-fs: Unrecognized mount option "errors=remount-rw" or missing value
mount: / not mounted already or bad option
mountall: mount / [511] terminated with status 32
mountall: Filesystem could not be mounted: /
init: mountall main process(493) terminated with status 4
Mount of root filesystem failed ...

Can you help me (with few experience with linux) to fix it?

Alternative could I return to my old version or at least restore my old data on the harddrive?

---

### Post by WorMzy on 2010-11-04
Like the error says, there's no such option as remount-rw. "errors=remount-ro" will remount the filesystem with read only permissions, and is the safest option. Set it to "errors=continue" if you really don't care about corrupting your data and making the partition unusable, or "errors=panic" if you're a Windows fan and miss the good 'ol BSOD-style system stopping errors. ;P

Oh yes, if you're not sure how to change it, boot into a LiveCD, open nautilus (file manager) and mount your linux partition. Then open a terminal and run "gksu gedit /media/[COLOR="Red"]<Linux partition's name/uuid>[/COLOR]/etc/fstab

Make the change, save and exit, then reboot.

---

### Post by P4man on 2010-11-04
The above poster is correct, but that may fly over your head if you are new to linux.

Boot from an ubuntu cd (or usb stick).  In places menu, select your harddrive.
Press alt+F2 to bring up the run dialogue. Type

```
gksudo gedit
```

This will launch a text editor with root permissions. 
In gedit go File > open
In the left pane select File system (which is the root, also known as "/"). Then browse to "/media". There a folder will represent your harddrive by a number or name. Open it. then continue to /media/yourharddive/etc/ and open the file fstab. /etc is an actual folder, I dont mean it as shorthand for etcetera. 

Make the changes suggested above, save, exit, reboot. If in doubt, post the contents of fstab here.

---

### Post by eawim on 2010-11-04
@wormzy: Apart from "mount your linux partition" I had no problems with the first answer. Because what to mount to which endpoint ... (with dh - h I see my partition). So I tried only the rest, unsuccessful.

@P4man: easier to understand - but ... the folder /Media is empty ... . What can I do now, should something be mounted before ...

I was working with jaunty jackalope and look and feel of 10.10 is a little bit different ...  Or shall I try LiveCD from 9.04 (not 10.10)?

Thanx in advance and kind regards

---

### Post by P4man on 2010-11-04
Yes the harddrive has to be mounted. If there is nothing wrong with the drive and filesystem, just accessing it from places menu should mount it automatically (and appear in /media). If that doesnt happen, then something may be wrong with the filesystem.

Can you post the output of

```
sudo fdisk -l
```

---

### Post by eawim on 2010-11-04
output from this command:
/dev/sda1 *(boot)       1        18992      14....            83     Linux
/dev/sda2            18663       19457          6385837     5      Erweiterte (=Extended)
/dev/sda5            18663       19457          6385806   82      Linux Swap / Solaris

---

### Post by P4man on 2010-11-04
Check the filesystem with:

```
fsck.ext4 -fpc /dev/sda1
```

WHile you are checking, check the drive for hardware problems. in system > administration > disk utility, select your harddrive and look at the SMART status.

---

### Post by eawim on 2010-11-04
I am checking the filesystem and put a "sudo" in front of 
-
the smartstatus is green - works. I saw there that the volume is not mounted (I hope I translate everything correct, because I'm working parallel with a german version, next time I start in english). When I try to mount that volume -> Error mounting: mount: /dev/sda1 already mounted or /media/ea038808 busy

---

### Post by P4man on 2010-11-04
so it should be mounted in /media/ea038808 
Is it not? If not what does

```
mount
```

tell you?

edit: perhaps fsck was still running... wait for it to finish

---

### Post by eawim on 2010-11-04
[FONT=&quot]I am afraid it is not - this is the result of  mount:
[/FONT]
[FONT=&quot]aufs on / type aufs (rw)[/FONT]  
 [FONT=&quot]none on /proc type proc (rw,noexec,nosuid,nodev)[/FONT]  
 [FONT=&quot]none on /sys type sysfs (rw,noexec,nosuid,nodev)[/FONT]
 [FONT=&quot]fusectl on /sys/fs/fuse/connections type fusectl (rw)[/FONT]
   [FONT=&quot]none on /dev type devtmpfs (rw,mode=0755)[/FONT]  
 [FONT=&quot]none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)[/FONT]  
 [FONT=&quot]/dev/sr0 on /cdrom type iso9660 (ro,noatime)[/FONT]  
 [FONT=&quot]/dev/loop0 on /rofs type squashfs (ro,noatime)[/FONT]  
 [FONT=&quot]none on /sys/kernel/debug type debugfs (rw)[/FONT]  
 [FONT=&quot]none on /sys/kernel/security type securityfs (rw)[/FONT]  
 [FONT=&quot]none on /dev/shm type tmpfs (rw,nosuid,nodev)[/FONT]  
 [FONT=&quot]tmpfs on /tmp type tmpfs (rw,nosuid,nodev)[/FONT]  
 [FONT=&quot]none on /var/run type tmpfs (rw,nosuid,mode=0755)[/FONT]  
 [FONT=&quot]none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)[/FONT]  
 [FONT=&quot]binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)[/FONT]  
 [FONT=&quot]gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)

mount without livecd is a little bit different:
/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc tpe proc (rw)
...

so sda1 is already mounted on ext3 - change from rw to ro took place but result is still the same
[/FONT]

---

### Post by eawim on 2010-11-05
Starting in recovery mode - I found another errormessage, so I had another look within the archives of this forum and here it is ->
[http://ubuntuforums.org/archive/index.php/t-1306203.html](http://ubuntuforums.org/archive/index.php/t-1306203.html)

deleting a few lines of code and Ubuntu is back again, working fine!   THANX TO ALL!

---

