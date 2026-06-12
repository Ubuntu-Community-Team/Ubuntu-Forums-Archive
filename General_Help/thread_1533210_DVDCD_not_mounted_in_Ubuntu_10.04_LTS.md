---
title: "DVD/CD not mounted in Ubuntu 10.04 LTS"
date: 2010-07-17
forum: General Help
---

### Post by cordnor on 2010-07-17
Installed from the DVD in question
Updated the system
When I try to burn another iso with Brasero, the system do not find the DVD.

**lshw -C disk**
  *-cdrom                 
       description: DVD-RAM writer
       product: DVDRW SSM-8515S
       vendor: Slimtype
       physical id: 0.0.0
       bus info: scsi@1:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/dvd
       logical name: /dev/dvdrw
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: GRS6
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 status=busy
 ...............
** in /etc/fstab**
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=4b3cd596-74cf-4a2a-b47d-bda532050a28 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=d2f6940e-3209-4af5-abe0-9cc2894ec925 none            swap    sw              0       0
.................
**ls -l /media**
total 0
.................

Anyone who can help me to setup so I can use the CD/DVD?

---

### Post by AlphaLexman on 2010-07-17
Is the drive mounted? What is the output of:
```
mount
```

---

### Post by cordnor on 2010-07-17
> **AlphaLexman said:**
> Is the drive mounted? What is the output of:
```
mount
```

Thanks for answering
 mount
/dev/sda1 on / type ext4 (rw,errors=remount-ro)
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
gvfs-fuse-daemon on /home/master/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=master)

Hoping for help here.

---

### Post by AlphaLexman on 2010-07-17
Try this:
```
sudo mkdir /media/CD
sudo mount /dev/scd0 /media/CD
```

---

### Post by cordnor on 2010-07-17
> **AlphaLexman said:**
> Try this:
```
sudo mkdir /media/CD
sudo mount /dev/scd0 /media/CD
```

sudo mkdir /media/CD

sudo mount /dev/scd0 /media/CD
mount: /dev/sr0: unknown device

---

### Post by AlphaLexman on 2010-07-17
I apologize, /dev/scd0 may not be your CD Drive Bay. it could be:

[LIST]
[*]/dev/cdrom
[*]/dev/cdrom1
[*]/dev/cdrw
[*]/dev/scd0
[*]/dev/scd1
[*]/dev/sr0
[*]/dev/sr1
[*]/dev/dvd
[*]/dev/dvd1
[/LIST]
But, in any case the drive is not mounted. It needs to be mounted before you will have read-write access to it.

---

### Post by cordnor on 2010-07-17
> **AlphaLexman said:**
> I apologize, /dev/scd0 may not be your CD Drive Bay. it could be:

[LIST]
[*]/dev/cdrom
[*]/dev/cdrom1
[*]/dev/cdrw
[*]/dev/scd0
[*]/dev/scd1
[*]/dev/sr0
[*]/dev/sr1
[*]/dev/dvd
[*]/dev/dvd1
[/LIST]
But, in any case the drive is not mounted. It needs to be mounted before you will have read-write access to it.

HI again,
I am brand new to ubuntu so I appreciate your help

Running the command dmesg | less I find the following about sr0
[    2.223590] scsi 1:0:0:0: CD-ROM            Slimtype DVDRW SSM-8515S  GRS6 PQ: 0 ANSI: 5
[    2.232965] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    2.232969] Uniform CD-ROM driver Revision: 3.20
[    2.233100] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    2.233176] sr 1:0:0:0: Attached scsi generic sg0 type 5

Does this help you giving me the correkt command to mount the DVD?

Hoping for answer.

---

### Post by AlphaLexman on 2010-07-17
Sorry if this is redundant, please post the output of:
```
sudo lshw -C disk
```

---

### Post by cordnor on 2010-07-17
> **AlphaLexman said:**
> Sorry if this is redundant, please post the output of:
```
sudo lshw -C disk
```

Here it is
sudo lshw -C disk
  *-cdrom                 
       description: DVD-RAM writer
       product: DVDRW SSM-8515S
       vendor: Slimtype
       physical id: 0.0.0
       bus info: scsi@1:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/dvd
       logical name: /dev/dvdrw
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: GRS6
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 status=busy
  *-disk
       description: ATA Disk
       product: Hitachi HTS54161
       vendor: Hitachi
       physical id: 0.0.0
       bus info: scsi@2:0.0.0
       logical name: /dev/sda
       version: SB4O
       serial: SB2441SJCA44RE
       size: 149GiB (160GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=0003dcc1

---

### Post by AlphaLexman on 2010-07-17
What happens when you put in cd/dvd that has data on it, i.e. an *.iso disc,

[INDENT]vs.
[/INDENT]
Inserting a blank cd-r ?

Does ubuntu auto-mount either one?

---

### Post by cordnor on 2010-07-17
> **AlphaLexman said:**
> What happens when you put in cd/dvd that has data on it, i.e. an *.iso disc,
[INDENT]vs.
[/INDENT]Inserting a blank cd-r ?

Does ubuntu auto-mount either one?

No, nothing happens with any of the options

And here are the fstab:
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=4b3cd596-74cf-4a2a-b47d-bda532050a28 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=d2f6940e-3209-4af5-abe0-9cc2894ec925 none            swap    sw              0       0

---

### Post by AlphaLexman on 2010-07-17
I am not an fstab expert, but try this:

```
sudo mount /dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
```

and post the results.

---

### Post by cordnor on 2010-07-17
> **AlphaLexman said:**
> I am not an fstab expert, but try this:

```
sudo mount /dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
```and post the results.

sudo mount /dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
[sudo] password for master: 
Usage: mount -V                 : print version
       mount -h                 : print this help
       mount                    : list mounted filesystems
       mount -l                 : idem, including volume labels
So far the informational part. Next the mounting.
The command is `mount [-t fstype] something somewhere'.
Details found in /etc/fstab may be omitted.
       mount -a [-t|-O] ...     : mount all stuff from /etc/fstab
       mount device             : mount device at the known place
       mount directory          : mount known device here
       mount -t type dev dir    : ordinary mount command
Note that one does not really mount a device, one mounts
a filesystem (of the given type) found on the device.
One can also mount an already visible directory tree elsewhere:
       mount --bind olddir newdir
or move a subtree:
       mount --move olddir newdir
One can change the type of mount containing the directory dir:
       mount --make-shared dir
       mount --make-slave dir
       mount --make-private dir
       mount --make-unbindable dir
One can change the type of all the mounts in a mount subtree
containing the directory dir:
       mount --make-rshared dir
       mount --make-rslave dir
       mount --make-rprivate dir
       mount --make-runbindable dir
A device can be given by name, say /dev/hda1 or /dev/cdrom,
or by label, using  -L label  or by uuid, using  -U uuid .
Other options: [-nfFrsvw] [-o options] [-p passwdfd].
For many more details, say  man 8 mount .

---

### Post by AlphaLexman on 2010-07-17
Sorry, that was UGLY!

---

### Post by cordnor on 2010-07-17
> **AlphaLexman said:**
> Sorry, that was UGLY!

OK
I have found the following thread:
[http://georgia.ubuntuforums.org/showthread.php?t=1503849](http://georgia.ubuntuforums.org/showthread.php?t=1503849)

and tried:

sudo mount -t iso9660 /dev/cdrom /media/cdrom/
mount: no medium found on /dev/sr0

I also have a /CDROM directory in root and tried:
sudo mount -t iso9660 /cdrom /media/cdrom/
mount: /cdrom is not a block device

Frustrated?  YES

---

### Post by AlphaLexman on 2010-07-17
Can you use the 'eject' command to open the CD drive bay?
```
eject /dev/scd0
```
or whatever /dev/cdrom, etc may be????

---

### Post by mc4man on 2010-07-17
A few ponts here - 
devices (a cd/dvd drive) do not get mounted

blank media (cd or dvd) and audio cd's don't get mounted - only accessed at a location

Only media (a cd or dvd) that has a filesystem gets mounted, ie the filesystem gets mounted, not the device

what's of interest from post 1 (lshw) is this
> configuration: ansiversion=5 status=busy


that seems to indicate blank media in the drive and the drive is busy (doing what who knows.

Try removing any media and rebooting, then insert a dvd or cd with a filesystem if you have one ( dvd movie, data dvd or data cd ) 
Then run sudo lshw -C disk and post

(brasero is always somewhat borked in some manner for some setups

---

### Post by AlphaLexman on 2010-07-17
With a little research, I may have missed an option...

Ooops, sorry!

Try this different code (added -o)

```
sudo mount -o /dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
```

---

### Post by cordnor on 2010-07-17
> **mc4man said:**
> A few ponts here - 
devices (a cd/dvd drive) do not get mounted

blank media (cd or dvd) and audio cd's don't get mounted - only accessed at a location

Only media (a cd or dvd) that has a filesystem gets mounted, ie the filesystem gets mounted, not the device

what's of interest from post 1 (lshw) is this



that seems to indicate blank media in the drive and the drive is busy (doing what who knows.

Try removing any media and rebooting, then insert a dvd or cd with a filesystem if you have one ( dvd movie, data dvd or data cd ) 
Then run sudo lshw -C disk and post

(brasero is always somewhat borked in some manner for some setups

Hi again
Sorry this took some time here is what I have done:
eject /dev/scd0  - works fine

sudo lshw -C disk
  *-cdrom                 
       description: DVD-RAM writer
       product: DVDRW SSM-8515S
       vendor: Slimtype
       physical id: 0.0.0
       bus info: scsi@3:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/dvd
       logical name: /dev/dvdrw
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: GRS6
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 status=nodisc
  *-disk
       description: ATA Disk
       product: Hitachi HTS54161
       vendor: Hitachi
       physical id: 0.0.0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
       version: SB4O
       serial: SB2441SJCA44RE
       size: 149GiB (160GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=0003dcc1

The status is now nodisk

Shuts down PC
Restarts PC

Inserting a DVD with normal content (diff files of type txt and html)
After some work opens the DVD in fileBrowser
Clicks on "places" /media/skole - eject and DVD ejects

tried use Brasero to burn iso image
DVD working very hard but Brasero do noe find the DVD
Cancel the operation and asks if I want to eject the DVDRW SSM-8515S
Unexpected error
command: eject /dev/scd0
after 1 minute it ejects

using the first DVD above ubuntu mounts and shows the content
Clicks on "places" /media/skole - eject and DVD ejects

on the File Browser > Computer I have 2 icons :
CD/DVD Drive
File System

Insert music CD and it mounts and opens

inserts new clean DVD disc
DVD player works very hard and then stops

Without taking the DVD disk out I start Brasero
Brasero do not find disc to write to
Cancel and quit Brasero
Have to use: eject /dev/scd0 to eject (2 minutes)

command: sudo lshw -C disk
shows exactly the same as in the start of this replay


OK now I can read DVDs but I still have not been able to burn an iso file.
And I can not use the Brasero obviously.



BUT, during this I have lost my number keypad - it is not working

---

### Post by baguahsing on 2010-07-17
I'm having a similar issue.  In disk manager, the cdrom is listed, so I'm assuming the drive is mounting.  It is listed as /dev/sr0 in disk manager.  Inserting media is hit and miss.  Sometimes it mounts the media (mounted in /media), most times the light on the drive flashes a few times and then stays on, the cd light on the laptop just flashes a few times.  If I go into terminal a tell it to mount /dev/sr0 I get an error something like no such device in /etc/fstab or /etc/mtab.  I remember reading something about 10.04 doesn't use fstab.  I'm a 2 week old noob, so please bear with me and be specific with your kind guidance.  I'm using the 10.04 netbook remix.

---

### Post by mc4man on 2010-07-17
> And I can not use the Brasero obviously.

Personally I don't use braseo though from time to time do as a test. Sometimes it works ok sometimes not 

(I use Imgburn in wine

You may want to find and try different apps, gnomebaker and k3b come to mind.

Otherwise there are ppa'a with some brasero builds or [replacements to some libs]("https://launchpad.net/~brandonsnider/+archive/cdrtools") that may improve brasero's usability


Edit:
to show what lshw should report  - first drive has blank dvd, 2nd has a data dvd
>  *-cdrom:0               
       description: DVD-RAM writer
       product: DVD A  DH20A4P
       vendor: ATAPI
       physical id: 0
       bus info: scsi@0:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/dvd
       logical name: /dev/dvdrw
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: 9P59
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 [COLOR="Blue"]status=ready[/COLOR]
     *-medium
          physical id: 0
          logical name: /dev/cdrom
  *-cdrom:1
       description: DVD reader
       product: DVD-ROM GDR8164B
       vendor: HL-DT-ST
       physical id: 1
       bus info: scsi@1:0.0.0
       logical name: /dev/cdrom1
       logical name: /dev/dvd1
       logical name: /dev/scd1
       logical name: /dev/sr1
       logical name: /media/cdrom1
       version: 0L06
       capabilities: removable audio dvd
       configuration: ansiversion=5 mount.[COLOR="Blue"]fstype=udf mount.options=ro,nosuid,nodev,relatime,utf8 state=mounted[/COLOR] status=ready
     *-medium
          physical id: 0
          logical name: /dev/cdrom1
          logical name: /media/cdrom1
          configuration: mount.fstype=udf mount.options=ro,nosuid,nodev,relatime,utf8 state=mounted

( I do use fstab entries for static mount points (/media/cdrom0. /media/cdrom1 but that shouldn't matter

You'll notice for the blank dvd there is no mountpoint shown under *-medium (nothing to mount), and for the data dvd the mountpoint is shown (/media/cdrom1

---

### Post by cordnor on 2010-07-17
Thanks a lot!
In the start I think it was the Brasero which locked the system for me.

My PCs version to your example
with empty tray:
       configuration: ansiversion=5 status=nodisc

with empty disk in tray
       configuration: ansiversion=5 status=busy

with data dvd in tray
       configuration: ansiversion=5 mount.fstype=iso9660 mount.options=ro,nosuid,nodev,relatime,uid=1000,gid=1000,iocharset=utf8,mode=0400,dmode=0500 state=mounted status=ready
     *-medium
          physical id: 0
          logical name: /dev/cdrom
          logical name: /media/Aspøy skole 2005
          configuration: mount.fstype=iso9660 mount.options=ro,nosuid,nodev,relatime,uid=1000,gid=1000,iocharset=utf8,mode=0400,dmode=0500 state=mounted

Great!

2 questions more (please)
What is the best way to burn an iso image from the commandline?

Any idea about how to reactivate my number keyboard. (on the right on a laptop)

---

### Post by cordnor on 2010-07-18
Hi again,        
Great help from AlphaLexman and mc4man, THANKS for using your time for us newbees!!!!

Hoping baguahsing also learned something here.
I learned a lot.

Closing as solved!

Have a great day!

---

### Post by DonThompson on 2010-07-18
OK. I'm glad that whatever was discussed worked for someone.  I don't get what the end result was, since most of the posts wandered through the details of the particular CD/DVD device, and issues with a burner program.

I still can't get the 10.04 server to mount a CD or a DVD WITH a file system on it.  Eject works.  Whoopee!  No wonder people get frustrated.  I get the nothing in fstab or mtab complaint, and nothing happens. :(

---

### Post by DonThompson on 2010-07-18
OK - in another thread I found this:

"sudo mount /dev/sr0 mnt"

and it worked for me.  Why does the documentation tell me: "sudo mount /media/cdrom0 -o unhide"?

---

### Post by baguahsing on 2010-07-18
Cdrom is mounting, just when I insert a cd, it will not auto mount, and I haven't been able to use terminal to manually mount. From terminal:
 
sudo lshw -C disk (tray open)
 
*-cdrom
description: DVD reader
product: DW-28E
vendor: TEAC
physical id: 1
bus info: scsi@1:0.0.0
logical name: /dev/cdrom
logical name: /dev/cdrw
logical name: /dev/dvd
logical name /dev/scd0
logical name /dev/sr0
version: 7.0A
serial: [TEAC DW-28E 7.0A
capabilities: removable audio cd-r cd-rw dvd
configuration: ansiversion=5 status=open 
 
sudo lshw -C disk (tray closed)
 
*-cdrom
description: DVD reader
product: DW-28E
vendor: TEAC
physical id: 1
bus info: scsi@1:0.0.0
logical name: /dev/cdrom
logical name: /dev/cdrw
logical name: /dev/dvd
logical name /dev/scd0
logical name /dev/sr0
version: 7.0A
serial: [TEAC DW-28E 7.0A
capabilities: removable audio cd-r cd-rw dvd
configuration: ansiversion=5 status=nodisc
 
sudo lshw -C disk (cd installed)
 
*-cdrom
description: DVD reader
product: DW-28E
vendor: TEAC
physical id: 1
bus info: scsi@1:0.0.0
logical name: /dev/cdrom
logical name: /dev/cdrw
logical name: /dev/dvd
logical name /dev/scd0
logical name /dev/sr0
version: 7.0A
serial: [TEAC DW-28E 7.0A
capabilities: removable audio cd-r cd-rw dvd
configuration: ansiversion=5 status=ready
*-medium
physical id: 0
logical name: /dev/cdrom
 
/etc/fstab only references the partitions on the hard drive
 
Sometimes inserting a cd/dvd it will auto mount or it may show in the system tray and I can left click and have the option to mount, but most times I get a few blinking lights and nothing happens.
 
The cd/dvd drive is recognized and mounted. Any medium I put is not. What next?

---

### Post by mc4man on 2010-07-18
> sudo lshw -C disk (cd installed)

*-cdrom
......
.......
configuration: ansiversion=5 status=ready
*-medium
physical id: 0
logical name: /dev/cdrom

What type of cd was in the drive? (blank, audio or data

---

### Post by baguahsing on 2010-07-18
It was a maximumpc cd from the magazine, so I guess data.

---

### Post by cordnor on 2010-07-19
Hi
I see that this is still going on.

I came over an article about CD and DVD discs that one should be aware of:
[http://en.wikipedia.org/wiki/DVD](http://en.wikipedia.org/wiki/DVD)

Check your CD/DVD device if it takes both -(minus) and + (plus) discs and check out what kind of disc you are using.

---

### Post by baguahsing on 2010-07-19
I haven't tried any dvds. Just a cd from a maximumpc magazine. Being new to linux (2-3 weeks) I may have been confused. Linux recognizes the drive. I thought that the drive gets mounted and any media inserted gets mounted or is it that the drive is recognized and any media is mounted. Either way the drive works. When I insert media, it may auto mount, I may get an icon in the sys tray or disk utility and I can click on to mount, or what happens quite a bit is the drive just sits there. Sometimes I have to open and close the tray a few times before the media is mounted. That's my issue, how do I get the media to be mounted most if not all the time? It could be that since I am using a older laptop the the drive is on its way out (Toshiba Satellite Pro 6100, P4 1.6Ghz cpu, 1Mb mem, 40Gb hard drive). I have not tried to burn a cd yet or play a dvd (cd-r, cd-rw, dvd-rom) The disk I have been using to t-shoot is for windows (yuk!). I've been wanting to try linux, finally did it a few weeks ago on this test bed laptop. Want to learn enough to divorce windows. Sorry for the long post.

---

### Post by cordnor on 2010-07-19
> **baguahsing said:**
> I haven't tried any dvds. Just a cd from a maximumpc magazine. Being new to linux (2-3 weeks) I may have been confused. Linux recognizes the drive. I thought that the drive gets mounted and any media inserted gets mounted or is it that the drive is recognized and any media is mounted. Either way the drive works. When I insert media, it may auto mount, I may get an icon in the sys tray or disk utility and I can click on to mount, or what happens quite a bit is the drive just sits there. Sometimes I have to open and close the tray a few times before the media is mounted. That's my issue, how do I get the media to be mounted most if not all the time? It could be that since I am using a older laptop the the drive is on its way out (Toshiba Satellite Pro 6100, P4 1.6Ghz cpu, 1Mb mem, 40Gb hard drive). I have not tried to burn a cd yet or play a dvd (cd-r, cd-rw, dvd-rom) The disk I have been using to t-shoot is for windows (yuk!). I've been wanting to try linux, finally did it a few weeks ago on this test bed laptop. Want to learn enough to divorce windows. Sorry for the long post.

Hi
Im rather new to Ubuntu myself.
When I go to meny > Places > Computer 
I find 2 icons : CD/DVD drive and File System.
Make sure the CD tray is closed when you boot. If not you probably will not find the CD/DVD drive icon.

When I now insert a CD og DVD it takes some time (up to 2 minutes) before the system mounts the filesystem and it shows up on the CD/DVD drive.

Then the CD disc you refer to. What kind of files are on it? It could be that it is intended for Microsoft and not Linux. I do not know if this can have anything to do with the problem.

Have you tried another CD?

---

### Post by baguahsing on 2010-07-19
When I get home I will try an audio cd.  Since you told me that it takes a couple of minutes to mount, maybe that is normal.  The cd I have been testing with is for windows.  I guess that I should fully test the drive and burn some sort of cd.

---

### Post by markcynt on 2010-07-20
Not sure if your problem is the same as mine but here is a fix that worked for me.

1) ```
gksu gedit /etc/default/grub
```

2) You will see a line that reads ***GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"***

3) Add ***noapic*** after ***quiet splash*** so it looks like this:```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash noapic"
```

4) Save the file then run```
sudo update-grub
```

5) Reboot

This fix has been working for me for about a month now.

---

### Post by BarryDocks on 2010-08-06
> **markcynt said:**
> Not sure if your problem is the same as mine but here is a fix that worked for me.

1) ```
gksu gedit /etc/default/grub
```

2) You will see a line that reads ***GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"***

3) Add ***noapic*** after ***quiet splash*** so it looks like this:```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash noapic"
```

4) Save the file then run```
sudo update-grub
```

5) Reboot

This fix has been working for me for about a month now.
Have the same problem on 2 different machines, one new dell laptop and an old AMD based system.  Tried this fix on the laoptop without success, in fact it would not boot at all until I changed the bios setting from ATA to APIC

---

### Post by BarryDocks on 2010-08-09
I have tried ubuntu studio and can confirm that this version mounts the CD-ROM without any problems

Only in with the 64bit edition on new hardware but not with the 32 bit edition on old hardware

---

