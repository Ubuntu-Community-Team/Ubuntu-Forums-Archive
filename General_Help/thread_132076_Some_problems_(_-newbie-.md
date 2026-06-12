---
title: "Some problems :( -newbie-"
date: 2006-02-17
forum: General Help
---

### Post by jc265 on 2006-02-17
First off, hello everyone.  I'm new to the world of linux.  I've searched the message boards for answers to my questions, but I can't find what I'm looking for.  

1 problem I have is playing media, either mp3, mpg, avi, anything.    When I try to open a movie or mp3, it loads in totem, and i get this message for both movies and mp3s...
[I]
Totem could not play 'file:///root/Desktop/file.whatever'.[/I]  <-- file.whatever was added by me :P
*Failed to play: Could not open resource for writing.*
How do I play my media?  What do I need to do to fix this?


Second.  My resolution.   I've searched, tried what ppl said to do, and still cant get my res to 1280x1024.  I'm using the SCEPTRE KOMODO II* X7 lcd monitor.  
[http://www.sceptre.com/Products/LCD/Specifications/spec_x7gKomodoII+.htm](http://www.sceptre.com/Products/LCD/Specifications/spec_x7gKomodoII+.htm)

Third, whats the command to start/enable my eth1?

And last on my want list...I would like to play window games on linux, someone told me about wine..where can I get a completely noob guide to install this?  I'm talkin a guide that will tell me everything to type because I'm still learning :)


Thank you for taking the time to read this.
Hope my noob questions don't annoy anyone. 

James

---

### Post by kaamos on 2006-02-17
0) are you logged in as root? REALLY bad idea!

1) To use mp3 and other patented formats -> [https://wiki.ubuntu.com/RestrictedFormats#head-7a73b076c82c7d7bb567bdac3322e53274f1d1f3](https://wiki.ubuntu.com/RestrictedFormats#head-7a73b076c82c7d7bb567bdac3322e53274f1d1f3)

3)
```
sudo ifdown eth1
sudo ifup eth1
```
A easier way is to go to *System->Administration->Network settings*

---

### Post by jc265 on 2006-02-17
wow thank you for the fast reply :)
I just got a new error when trying to play media files.. 
Says I don't have permission..how do I get permission?

---

### Post by kaamos on 2006-02-17
Where are the files? So are you trying to play files that are on your desktop (aka /home/yourusername/Desktop [where username is not root..]) ?

---

### Post by jc265 on 2006-02-17
mostly I'm trying to play them from a separate hard drive using NTFS, but windows is not on it.  Its my 2nd HD for media files and such

---

### Post by jc265 on 2006-02-17
I'm using the 64 bit ubuntu if that makes any difference =\

---

### Post by kaamos on 2006-02-17
As a security measure, the ubuntu installers makes non-system drives accessible only to root user. Look here to mount them automatically for everyone -> [http://ubuntuguide.org/#automountntfs](http://ubuntuguide.org/#automountntfs)

---

### Post by jc265 on 2006-02-17
I did that a few days ago, and everything is still read only :(  What am I doing wrong?

---

### Post by kaamos on 2006-02-17
That exactly enables _reading_ for everyone. Wrinting to ntfs is not (safely) supported in linux because ms has never published how ntfs works. :(

But you should be able to play media from them though.

---

### Post by jc265 on 2006-02-17
when i go to look at the media on the drive, they still have the red X over them and I still get the 'you do not have permission to view' message :(

---

### Post by kaamos on 2006-02-17
can you post the output of this command
```
cat /etc/fstab
```

---

### Post by jc265 on 2006-02-17
this is so confusing..i can get to the drive 2 ways, one way the files have the X on them, the other, they don't have the X, but I still get the recource error.  ARGH

---

### Post by jc265 on 2006-02-17
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda3       /home           reiserfs defaults        0       2
/dev/hda1       /media/hda1     ntfs    defaults        0       0
/dev/hdb1       /media/hdb1     ntfs    defaults        0       0
/dev/hda4       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdc        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/hda1       /media/windows  ntfs    nls=utf8,umask=0222 0       0
/dev/hdb1       /media/windows  ntfs    nls=utf8,umask=0222 0       0

---

### Post by kaamos on 2006-02-17
You have duplicate lines, type
```
sudo gedit /etc/fstab
```
edit the two bolded lines to look like below and remove the last two. Then save the file and reboot.


# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
/dev/hda2 / ext3 defaults,errors=remount-ro 0 1
/dev/hda3 /home reiserfs defaults 0 2
**/dev/hda1 /media/hda1 ntfs nls=utf8,umask=0222 0 0**
**/dev/hdb1 /media/hdb1 ntfs nls=utf8,umask=0222 0 0**
/dev/hda4 none swap sw 0 0
/dev/hdd /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/hdc /media/cdrom1 udf,iso9660 user,noauto 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto 0 0
[I]/dev/hda1 /media/windows ntfs nls=utf8,umask=0222 0 0
/dev/hdb1 /media/windows ntfs nls=utf8,umask=0222 0 0[/I]

---

### Post by jc265 on 2006-02-17
ok, i edited the 2 lines and removed the last 2, ctrl+alt+backspace, and now im back.  I try again to run the media, and still same error =\  

The 2 icons on my desktop, hda1 and hdb1, when i double click them i get the "You do not have the permissions necessary to view the contents of "hda1"." message..but when i go      system>>admin>>disks>>partitions>>browse  I can see everything on my drives, but still no go on playing anything.  Could my media player app be messing up somehow?

---

### Post by kaamos on 2006-02-17
If you go throught admin, you have root access. So the permissions are still not right.

Ok, backup you fstab like this
```
sudo cp /etc/fstab /etc/fstab.bak
```
Then type```
sudo gedit /etc/fstab
```
and replace the contents with this:

# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
/dev/hda2 / ext3 defaults,errors=remount-ro 0 1
/dev/hda3 /home reiserfs defaults 0 2
/dev/hda1 /media/hda1 ntfs ro,nls=utf8,auto,uid=1000,gid=1000 0 0
/dev/hdb1 /media/hdb1 ntfs ro,nls=utf8,auto,uid=1000,gid=1000 0 0
/dev/hda4 none swap sw 0 0
/dev/hdd /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/hdc /media/cdrom1 udf,iso9660 user,noauto 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto 0 0[/code]

Then reboot. If it is still not working, post the output of the command "mount" and "ls -la /media"

---

### Post by jc265 on 2006-02-17
mount
```
/dev/hda2 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /dev/shm type tmpfs (rw)
usbfs on /proc/bus/usb type usbfs (rw)
tmpfs on /lib/modules/2.6.12-9-amd64-generic/volatile type tmpfs (rw,mode=0755)
/dev/hda3 on /home type reiserfs (rw)
/dev/hda1 on /media/hda1 type ntfs (rw)
/dev/hdb1 on /media/hdb1 type ntfs (rw)
tmpfs on /dev type tmpfs (rw,size=10M,mode=0755)
/dev/hdd on /media/cdrom0 type iso9660 (ro,noexec,nosuid,nodev,user=a64)

```

ls -la /media
```
total 34
drwxr-xr-x   8 root root 4096 2006-01-27 10:09 .
drwxr-xr-x  23 root root 4096 2006-01-27 01:08 ..
lrwxrwxrwx   1 root root    6 2006-01-26 18:31 cdrom -> cdrom0
dr-xr-xr-x   1 root root 2048 2004-07-14 13:10 cdrom0
drwxr-xr-x   2 root root 4096 2006-01-26 18:31 cdrom1
lrwxrwxrwx   1 root root    7 2006-01-26 18:31 floppy -> floppy0
drwxr-xr-x   2 root root 4096 2006-01-26 18:31 floppy0
dr-x------   1 root root 8192 2006-02-16 06:00 hda1
dr-x------   1 root root 4096 2006-02-16 06:00 hdb1
drwxr-xr-x   2 root root 4096 2006-01-27 10:09 windows

```

---

### Post by kaamos on 2006-02-17
Both not good. :D

> /dev/hda1 on /media/hda1 type ntfs (r**w**)
shouldn certainly not have rw

> dr-x------   1 root root 8192 2006-02-16 06:00 hda1
dr-x------   1 root root 4096 2006-02-16 06:00 hdb1
These have wrong permissions. Try ```
sudo chmod +r /media/hda1
sudo chmod +r /media/hdb1
```

And please post your fstab again.

---

### Post by jc265 on 2006-02-17
```
# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
/dev/hda2 / ext3 defaults,errors=remount-ro 0 1
/dev/hda3 /home reiserfs defaults 0 2
/dev/hda1 /media/hda1 ntfs ro,nls=utf8,auto,uid=1000,gid=1000 0 0
/dev/hdb1 /media/hdb1 ntfs ro,nls=utf8,auto,uid=1000,gid=1000 0 0
/dev/hda4 none swap sw 0 0
/dev/hdd /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/hdc /media/cdrom1 udf,iso9660 user,noauto 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto 0 0


```

oh and btw, thank you for helping me so far with this :)

guess i should have added im still locked out and media wont play huh :P

---

### Post by kaamos on 2006-02-17
Don't thank yet since I'm fast running out of ideas..
You have rebooted since making changes to /etc/fstab and "mount" still shows the rw with the ntfs lines? That sounds quite strange.

You could try mounting the volume manually
```
sudo umount /dev/hda1
sudo mkdir /media/temp
sudo chmod 555 /media/temp
sudo mount /dev/hda1 /media/temp -t ntfs -o nls=utf8,umask=0222
```

---

### Post by jc265 on 2006-02-17
hey hey hey, it lets me play stuff on hda1
how do i access hdb1? i tried the same commands but with hdb1 in the command lines, but it says temp already exists.  

oh and when i play video, its just audio..i missing a codec?

---

### Post by kaamos on 2006-02-17
hdb1:
```
sudo umount /dev/hdb1
sudo mkdir /media/temp2
sudo chmod 555 /media/temp2
sudo mount /dev/hdb1 /media/temp2 -t ntfs -o nls=utf8,umask=0222
```

For video, have you installed the codecs mentioned in the restrictedformats wiki page? Except for w32codecs since it does not work with 64bit systems. I'm not shure if there is some workaround for this though.

---

