---
title: "Do I need to move to my Windows partition to read my DVD?"
date: 2006-06-14
forum: General Help
---

### Post by Hoffmann on 2006-06-14
Hello Guys,

A couple of days ago I posted a message regarding a problem I am having to read my data (back up) DVD. Well, it seems like no one was able to answer me, and I decided to post this message once again. I think I wouldn't need to move to my Windows partition to do that - it would be ridiculous. I think Ubuntu is better than Windows :) 

Actually, before upgrading from Breezy to Dapper, I was able to read my DVD without problem. The problem started after the upgrading. With Dapper, I get no problem for reading CDs. My problem is JUST with DVDs.

When I try to read the DVD I get:
>  You do not have the permissions necessary to view the contents of "dvdrecorder". 

Ok. I checked the permissions, and I got:
>  total 18
lrwxrwxrwx 1 root root 6 2006-05-29 15:30 cdrom -> cdrom0
drwxr-xr-x 2 root root 4096 2006-05-29 15:30 cdrom0
drwxr-xr-x 2 root root 4096 2006-05-29 15:30 cdrom1
dr-xr-x--- 33 root root 1804 2006-05-13 12:00 dvdrecorder
drwxr-xr-x 12 root root 4096 1969-12-31 18:00 sda1
drwxr-xr-x 2 root root 4096 2006-05-29 15:30 sda2 

I have changed the permission of dvdrecorder, but I am still having problems. Bofore I forget trying to read my DVD on Ubuntu, can anyone, please, give me a hint about that? Should I install any library? What am I missing?

---

### Post by mscman on 2006-06-14
Can you post the output of 
```
cat /etc/fstab
```?
Sounds like this file was changed during your upgrade

---

### Post by Hoffmann on 2006-06-14
[QUOTE=mscman]Can you post the output of 
```
cat /etc/fstab
```?
Sounds like this file was changed during your upgrade[/QUOTE]

It is:
> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda3       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda1       /media/sda1     vfat    defaults        0       0
/dev/sda2       /Windows        ntfs    auto,users,rw,umask=0022       0       0
/dev/sda5       none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto     0       0
 

What do you think?

---

### Post by scxtt on 2006-06-14
> Ok. I checked the permissions, and I got:

[indent]total 18
lrwxrwxrwx 1 root root 6 2006-05-29 15:30 cdrom -> cdrom0
drwxr-xr-x 2 root root 4096 2006-05-29 15:30 cdrom0
drwxr-xr-x 2 root root 4096 2006-05-29 15:30 cdrom1
dr-xr-x--- 33 root root 1804 2006-05-13 12:00 dvdrecorder
drwxr-xr-x 12 root root 4096 1969-12-31 18:00 sda1
drwxr-xr-x 2 root root 4096 2006-05-29 15:30 sda2[/indent]

I have changed the permission of dvdrecorder, but I am still having problems. Bofore I forget trying to read my DVD on Ubuntu, can anyone, please, give me a hint about that? Should I install any library? What am I missing?do you mean you changed it to "dr-xr-xr-x" because otherwise you won't be able to read to it as "other" ... it could probably also stand to be writable, if you want to record w/ it ... did you add /media/dvdrecorder yourself?  and how many optical drives do you have/use?  looks like you have 2 (cdrecorder and dvdrecorder?)  cause it will also come down to the program you're using and which drive you're telling it to use (most default to /media/cdrom - which is a link to /media/cdrom0 - but it's generally easier to specify the device itself /dev/[h,s]d*) ...

also, your /etc/fstab is using:

[indent]/dev/scd1 /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/scd0 /media/cdrom1 udf,iso9660 user,noauto 0 0[/indent]which makes no mention of /media/dvdrecorder ... you should be using /media/cdrom (according to your fstab) ...

---

### Post by Hoffmann on 2006-06-14
[QUOTE=scxtt]do you mean you changed it to "dr-xr-xr-x" because otherwise you won't be able to read to it as "other" ... it could probably also stand to be writable, if you want to record w/ it ... did you add /media/dvdrecorder yourself?  and how many optical drives do you have/use?  looks like you have 2 (cdrecorder and dvdrecorder?)  cause it will also come down to the program you're using and which drive you're telling it to use (most default to /media/cdrom - which is a link to /media/cdrom0 - but it's generally easier to specify the device itself /dev/[h,s]d*) ...

also, your /etc/fstab is using:

[indent]/dev/scd1 /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/scd0 /media/cdrom1 udf,iso9660 user,noauto 0 0[/indent]which makes no mention of /media/dvdrecorder ... you should be using /media/cdrom (according to your fstab) ...[/QUOTE]


When I use the second optical drive (DVD-ROM) , I get:
> You do not have the permissions necessary to view the contents of "usbdisk".
Moreover, on /etc/fstab, I have:

> <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda3       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda1       /media/sda1     vfat    defaults        0       0
/dev/sda2       /Windows        ntfs    auto,users,rw,umask=0022       0       0
/dev/sda5       none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto     0       0

I am still having problems. If anyone could give me a hint about that, I will be grateful.

---

### Post by scxtt on 2006-06-15
there is no good reason you should receive a message like "You do not have the permissions necessary to view the contents of "usbdisk"." unless your DVD-ROM is an external USB drive, is that the case?

as far as your /etc/fstab goes - you need to figure out what /dev designation your drive has - cause your /etc/fstab doesn't add up ...

why does /dev/scd1 point to /media/cdrom0?
why does /dev/scd0 point to /media/cdrom1?

how would your cdrom or dvd-rom be split into partitions? (it should be something like /dev/sca, /dev/scb, etc.) ...

if it's an internal IDE drive, it should have a /dev/hd* designation ...

---

### Post by Ramses de Norre on 2006-06-15
Looks like your fstab is pretty messed up.. Could you tell us your exact setup of harddisks and optical drives and which device nodes (/dev/something) they have?

---

### Post by Hoffmann on 2006-06-15
[QUOTE=scxtt]there is no good reason you should receive a message like "You do not have the permissions necessary to view the contents of "usbdisk"." unless your DVD-ROM is an external USB drive, is that the case?

as far as your /etc/fstab goes - you need to figure out what /dev designation your drive has - cause your /etc/fstab doesn't add up ...

why does /dev/scd1 point to /media/cdrom0?
why does /dev/scd0 point to /media/cdrom1?

how would your cdrom or dvd-rom be split into partitions? (it should be something like /dev/sca, /dev/scb, etc.) ...

if it's an internal IDE drive, it should have a /dev/hd* designation ...[/QUOTE]

My DVD-ROM is NOT an external USB drive. Since I upgrade to Dapper this has been my only problem. On Breezy my DVD-ROM worked fine.
I am really confuse now. :confused: 
I would appreciate a lot a way to solve this.

---

### Post by Hoffmann on 2006-06-15
[QUOTE=scxtt]there is no good reason you should receive a message like "You do not have the permissions necessary to view the contents of "usbdisk"." unless your DVD-ROM is an external USB drive, is that the case?

as far as your /etc/fstab goes - you need to figure out what /dev designation your drive has - cause your /etc/fstab doesn't add up ...

why does /dev/scd1 point to /media/cdrom0?
why does /dev/scd0 point to /media/cdrom1?

how would your cdrom or dvd-rom be split into partitions? (it should be something like /dev/sca, /dev/scb, etc.) ...

if it's an internal IDE drive, it should have a /dev/hd* designation ...[/QUOTE]


I decided to install KDE to see if my problem would be GNOME related. Ok. Now, after inserting the DVD, I get 
>  Could not enter folder /media/hda. 

---

### Post by scxtt on 2006-06-16
have you tried running your media playing program as root? i.e.:
```
sudo xine
```or something like that - should solve any permission issues ... tho doesn't help much w/ the root cause [no pun intended] ... do you have this problem in "live cd" mode?

---

### Post by Hoffmann on 2006-06-16
[QUOTE=scxtt]have you tried running your media playing program as root? i.e.:
```
sudo xine
```or something like that - should solve any permission issues ... tho doesn't help much w/ the root cause [no pun intended] ... do you have this problem in "live cd" mode?[/QUOTE]

I am talking about a data DVD, not a video/movie DVD.
I am really disapointed with this issue.....

---

### Post by scxtt on 2006-06-16
ahh, i'm so used to video/movie issues ...

what about in "live cd" mode?

i had "issues" as well w/ a breezy [font=courier]-->[/font] dapper upgrade, if things are good in live mode, is a reinstall (not upgrade) and option? -- yes, it's a shame upgrade causes issues - but what can you do?

---

### Post by Hoffmann on 2006-06-16
[QUOTE=scxtt]ahh, i'm so used to video/movie issues ...

what about in "live cd" mode?

i had "issues" as well w/ a breezy [font=courier]-->[/font] dapper upgrade, if things are good in live mode, is a reinstall (not upgrade) and option? -- yes, it's a shame upgrade causes issues - but what can you do?[/QUOTE]
Sorry for the 'stupid' question, but how can I run this "stuff" on live CD? I cannot to unistall my distro now. Can you explain how can I use live CD to try to fix this problem?
Thanks!

---

### Post by scxtt on 2006-06-16
the "Desktop" CD is a "live CD" meaning you can boot from it and get a working version of Ubuntu w/o affecting your hard drive in any way ... so i'm saying if your DVD drive acts as normal (and if you can post the /etc/fstab when using the live cd) we may be able to get to the bottom of why your fstab isn't adding up or making sense ... it also seems that your user setting have been messed up, i.e. the permission issues ...

---

### Post by Hoffmann on 2006-06-16
[QUOTE=scxtt]the "Desktop" CD is a "live CD" meaning you can boot from it and get a working version of Ubuntu w/o affecting your hard drive in any way ... so i'm saying if your DVD drive acts as normal (and if you can post the /etc/fstab when using the live cd) we may be able to get to the bottom of why your fstab isn't adding up or making sense ... it also seems that your user setting have been messed up, i.e. the permission issues ...[/QUOTE]
How can I boot from the live CD without reinstalling Ubuntu? Should I inserte the CD on the CD drive from ubuntu and reboot the machine? Sorry, probably the question maight seem stupid....

---

### Post by scxtt on 2006-06-16
it's cool man, the concept of a Live CD didn't make sense to me the 1st time i heard about it ... yeah, just insert the CD, reboot your machine and let it work its magic ... note that your BIOS has to support booting from a bootable CD (which the Live CD is) ...

---

### Post by Hoffmann on 2006-06-16
[QUOTE=scxtt]it's cool man, the concept of a Live CD didn't make sense to me the 1st time i heard about it ... yeah, just insert the CD, reboot your machine and let it work its magic ... note that your BIOS has to support booting from a bootable CD (which the Live CD is) ...[/QUOTE]
OK....I am looking for the live CD download now. Do you have the link? What I am getting is the "true" installation CD on Ubuntu download site.

---

### Post by scxtt on 2006-06-16
[here's one](http://mirror.cs.umn.edu/ubuntu-releases/6.06/ubuntu-6.06-desktop-i386.iso) ... make sure you get the "Desktop CD" ...

[here's a torrent](http://mirror.cs.umn.edu/ubuntu-releases/6.06/ubuntu-6.06-desktop-i386.iso.torrent)

this assumes you have an Intel (X86) based system ...

---

### Post by Hoffmann on 2006-06-16
[QUOTE=scxtt][here's one](http://mirror.cs.umn.edu/ubuntu-releases/6.06/ubuntu-6.06-desktop-i386.iso) ... make sure you get the "Desktop CD" ...

[here's a torrent](http://mirror.cs.umn.edu/ubuntu-releases/6.06/ubuntu-6.06-desktop-i386.iso.torrent)

this assumes you have an Intel (X86) based system ...[/QUOTE]
Ok..As I expected, it is the same 'true" installation CD...
I am running the live CD..
On /etc/fstab I have:
> unionfs / unionfs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
/dev/sda5 swap swap defaults 0 0
.What should I do now?

---

### Post by scxtt on 2006-06-16
can you view the contents of the CD / DVD?  do you have any visibility to the optical drive @ all?

---

### Post by Hoffmann on 2006-06-16
[QUOTE=scxtt]can you view the contents of the CD / DVD?  do you have any visibility to the optical drive @ all?[/QUOTE]
On /media, I have nothing

On /cdrom, I have:
> autorun.inf  disctree  isolinux    pool      README.diskdefines  start.ini
bin          dists     md5sum.txt  preseed   start.bmp           ubuntu
casper       install   pics        programs  start.exe           ubuntu.ico
 

I see no DVD-Rom....

---

### Post by scxtt on 2006-06-16
/cdrom looks to be the contents of the Live CD disk ... (wonder what "start.exe" is in there for (maybe ubuntu disks do something in windows?) - there is a autorun.inf, anyway) ... is the Live CD in your CD-ROM or DVD-ROM?

---

### Post by Hoffmann on 2006-06-16
[QUOTE=scxtt]/cdrom looks to be the contents of the Live CD disk ... (wonder what "start.exe" is in there for (maybe ubuntu disks do something in windows?) - there is a autorun.inf, anyway) ... is the Live CD in your CD-ROM or DVD-ROM?[/QUOTE]
The live CD is in my DVD-ROM:confused:

---

### Post by Hoffmann on 2006-06-16
scxtt,

I need to go now. Let's continue our conversation another time?
Good night!

---

### Post by scxtt on 2006-06-16
i've booted to a Live CD (not ubuntu, but symphony) and i'm able to use my DVD±RW w/o problems ... my /etc/fstab looks like this:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda2       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
devpts /dev/pts devpts gid=5,mode=620 0 0 # Auto-Update
[color=red]/dev/hdb /mnt/hdb_cdrom iso9660 noauto,users,exec 0 0 # Auto-Update[/color]
/dev/sda1 /mnt/sda1 ext3 auto,users,suid,dev,exec 0 0 # Auto-Update
/dev/sda2 /mnt/sda2 swap auto,users,suid,dev,exec 0 0 # Auto-Update
/dev/sdb1 /mnt/sdb1 ext3 auto,users,suid,dev,exec 0 0 # Auto-Update
/dev/sda2 swap swap defaults 0 0 # Auto-Update
/dev/fd0 /mnt/floppy vfat,msdos noauto,users,suid,dev,exec 0 0 # Auto-Update
```and my /dev/hdb {dvd drive} is recognized correctly ... i think what we'll need you to do is to look VERY closely when your Live CD is booting and find out how your DVD is being assigned ... i was able to see mine listed by the manufacturers name, see if you can do the same ...

also, in case i haven't asked before - is this and IDE DVD drive? - if it is, we should be looking for a /dev/hd* designation ...

---

