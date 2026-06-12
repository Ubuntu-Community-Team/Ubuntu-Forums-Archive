---
title: "Unable to play Audio CD's or Video DVD's"
date: 2010-05-24
forum: General Help
---

### Post by ost2life on 2010-05-24
Okay, I'm going to try this forum since I've had no luck in multimedia and video. I'm totally unable to play or mount audio CDs and unable to use video DVD's on my box right now. When I insert an audio CD I get a dialog box saying:

Unable to mount disc: Location is not mountable

and if I check **messages** in the Log File Viewer I see the following text repeated (save for the last line) a couple of dozen times.

```
May 24 13:04:37 Amber kernel: [ 6680.434685] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
May 24 13:04:37 Amber kernel: [ 6680.434691] sr 0:0:0:0: [sr0] Sense Key : Illegal Request [current] 
May 24 13:04:37 Amber kernel: [ 6680.434695] sr 0:0:0:0: [sr0] Add. Sense: Illegal mode for this track
May 24 13:04:37 Amber kernel: [ 6680.434702] sr 0:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 02 00
May 24 13:04:37 Amber kernel: [ 6680.434713] __ratelimit: 15 callbacks suppressed
```

"Audio Disc" shows up in "Places" but when I click it, I get the same message about mounting

on a similar but ultimately unrelated thread someone was asked to enter a few commands so I tried them and the following was the output:

```
main@Amber:~$ ls /dev/scd*
/dev/scd0
main@Amber:~$ sudo mount /dev/cdrom /media/cdrom0
[sudo] password for main: 
mount: block device /dev/sr0 is write-protected, mounting read-only
mount: you must specify the filesystem type
main@Amber:~$ sudo eject /dev/scd0
main@Amber:~$ sudo eject /dev/cdrom

```

both eject commands work by the way.

when I insert a DVD (For this example I'm using Three To Tango, don't judge me) **messages** shows the following:

```
May 24 13:12:13 Amber kernel: [ 7136.523804] cdrom: sr0: mrw address space DMA selected
May 24 13:12:13 Amber kernel: [ 7136.589328] cdrom: sr0: mrw address space DMA selected
May 24 13:12:14 Amber kernel: [ 7136.758900] UDF-fs: Partition marked readonly; forcing readonly mount
May 24 13:12:14 Amber kernel: [ 7136.791794] UDF-fs INFO UDF: Mounting volume 'THREE_TO_TANGO', timestamp 2000/04/12 22:26 (103c)
```

It mounts properly and I can browse the folder, however if I try to play the movie in Totem, it throws up the following error: 

An error occurred: Could not open location; you might not have permission to open the file.

As far as I can tell I have the relevant CSS libraries installed

Please help me as I'm lost without being able to play CD's and DVD's on my system.

---

### Post by ost2life on 2010-05-24
bump

---

### Post by wojox on 2010-05-24
Do you have the mdeibuntu repo's installed?

[http://wojox.homelinux.org/?p=12](http://wojox.homelinux.org/?p=12)

---

### Post by ost2life on 2010-05-24
No, I hadn't.
I followed the instructions on the page and the only package non-free-codecs actually installed as well was w32codecs. 19 other packages were left unchanged.

Still no dice on playing either Audio CDs or Video DVDs

```
May 24 18:39:16 Amber kernel: [26759.479812] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
May 24 18:39:16 Amber kernel: [26759.479820] sr 0:0:0:0: [sr0] Sense Key : Illegal Request [current] 
May 24 18:39:16 Amber kernel: [26759.479825] sr 0:0:0:0: [sr0] Add. Sense: Read of scrambled sector without authentication
May 24 18:39:16 Amber kernel: [26759.479832] sr 0:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 01 1c 00 00 08 00
```

that message came up when trying to play the DVD though.

---

### Post by ost2life on 2010-05-24
bump

---

### Post by nothingspecial on 2010-05-24
[[COLOR="Magenta"]This[/COLOR]]("http://ubuntuforums.org/showthread.php?t=766683") might help.

---

### Post by ost2life on 2010-05-25
I'm sorry, but I'm not sure what installing non-free codecs has to do with not being able to play audio cd's...something I was able to do with no problem on previous versions.
I've followed the instructions but still no dice.

---

### Post by MooPi on 2010-05-25
Can you display your /etc/fstab file contents to see if it needs to be edited.
Mine looks like this:
> # /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=c4e3930d-4c82-4e9f-a07c-6eddbc6c637e /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=ad769150-5a18-498d-afd6-494ea3d015b9 none            swap    sw              0       0
# /dev/sda3 Label=Bin1
UUID="951548cf-a0aa-4adb-80c3-3f8706c1003f /media/Bin1    ext4    user,auto       0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

---

### Post by ost2life on 2010-05-25
my fstab:

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
UUID=eb24ea7b-7629-4f0d-81d6-f280c4b34b2d /               ext3    errors=remount-ro 0       1
# swap was on /dev/sdd2 during installation
UUID=67808b8a-e014-455e-be09-91920e48174b none            swap    sw              0       0
UUID=5e38f7a8-10b8-49d2-b79f-28683f65da2d /media/Big\040Mama	ext2	defaults	0	0
UUID=f8736f39-8c8d-41ea-8c2f-7db847351b33 /media/Stanley	ext3	defaults	0	0
UUID=c898db1d-bcd4-4759-80c0-f763dd29535f /media/Karen		ext2	defaults	0	0
UUID=9ca21534-ebf2-4709-b36a-d8726ec822f1 /media/MP3		ext3	defaults	0	0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
```

---

### Post by MooPi on 2010-05-25
fstab looks normal. What type of drive is it Brand / sata / pata with the flat IDE cable ?

---

### Post by ost2life on 2010-05-25
Could it be that the drive has packed up?

if I put in a blank disc I get the same Sense Key Illegal requests messages.


```
May 25 21:04:10 Amber kernel: [ 4764.864917] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
May 25 21:04:10 Amber kernel: [ 4764.864932] sr 0:0:0:0: [sr0] Sense Key : Illegal Request [current] 
May 25 21:04:10 Amber kernel: [ 4764.864942] sr 0:0:0:0: [sr0] Add. Sense: Logical block address out of range
May 25 21:04:10 Amber kernel: [ 4764.864954] sr 0:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 01 00
May 25 21:04:10 Amber kernel: [ 4764.864983] __ratelimit: 15 callbacks suppressed
May 25 21:04:10 Amber kernel: [ 4764.872317] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
May 25 21:04:10 Amber kernel: [ 4764.872330] sr 0:0:0:0: [sr0] Sense Key : Illegal Request [current] 
May 25 21:04:10 Amber kernel: [ 4764.872340] sr 0:0:0:0: [sr0] Add. Sense: Logical block address out of range
May 25 21:04:10 Amber kernel: [ 4764.872350] sr 0:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 01 00
```

---

### Post by MooPi on 2010-05-25
You may just need to replace the drive cables or insure that everything is connected properly. If it is an older IDE drive and the drive jumper pin is in the wrong location it could be messing things up.

---

### Post by ost2life on 2010-05-25
it's suprising if that's the case, because as I said, it was fine on previous versions of Ubuntu. It only seems to have happened since the upgrade.

---

### Post by ost2life on 2010-05-31
Okay, still nothing happening.
Since my last post on the issue I found some instructions recommending a downgrade of some udev packages

libgudev-1.0-0_151-5_i386
udev_151-5_i386
libudev0_151-5_i386

other users said that this had helped them in the bug report I was looking at, however even after a restart I'm stuck with the same problem.
This time however, I get the following in "messages" in my Log File Viewer, sometimes 20 odd times depending on the disk:

May 31 23:55:13 Amber kernel: [  124.265924] VFS: busy inodes on changed media or resized disk sr0

Before I get the old messages about callback suppressed and illegal requests.. 

Please help me! :(

---

### Post by ost2life on 2010-05-31
bump

---

### Post by lidex on 2010-05-31
Worth a shot... go to 'System>Administration>Users and Groups' and make sure your user is a member of the 'cdrom' group.

---

### Post by ost2life on 2010-05-31
yep, I am. Sorry.

---

### Post by lidex on 2010-05-31
Maybe some help here:
[http://superuser.com/questions/49358/ubuntu-9-04-ripping-cds-with-grip]("http://superuser.com/questions/49358/ubuntu-9-04-ripping-cds-with-grip")

---

### Post by fancypiper on 2010-05-31
Perhaps one or both of these will help:

[Comprehensive Multimedia & Video Howto](http://ubuntuforums.org/showthread.php?t=766683)

[What To Do After A Fresh Ubuntu Install: A Script For Ubuntu 10.04 Lucid Lynx](http://www.webupd8.org/2010/04/what-to-do-after-fresh-ubuntu-install.html)

---

### Post by techunit on 2010-05-31
Ok you probably don't have restricted extras installed. what you got to do:

Go to Software Center And Install "Ubuntu Restricted Extras"

no put this code in for dvds ( I know your message is about Audio CDs but worked for me.

```
sudo /usr/share/doc/libdvdread4/install-css.s
```

This should work

---

### Post by ost2life on 2010-06-01
Thanks for the suggestions. Just to clear a couple of things up though, I'm not running a fresh 10.04 installation. This is an upgrade from 9.10, which was a fresh installation.

When I try to play the audio disc in Totem directly, I get the "Totem was not able to play the disc, the location was not mountable"

The connections to the drive are fine, I'm able to run bootable discs (including a live CD of ubuntu) no problem.

The last thing I want to do is to have to wipe the installation and start over as aside from this issue, I'm more than happy with the way things are now. But I really want to get this problem sorted out.

---

### Post by ost2life on 2010-06-01
bump

---

### Post by Swagman on 2010-06-01
If it were me I'd borrow another drive from .. anywhere just to see if my drive was buggered.

btw... That's exactly what I had to do last week. When I removed my Sony DVDRW the sticker on top said 2003 so I guess I had a good run out of it.

---

### Post by gator2802 on 2010-06-01
If you can confirm that you have added the restricted drivers and your drive worked in 9.10 then you need to recheck that a driver was not blacklisted during the upgrade process.

---

### Post by ost2life on 2010-06-01
> **Swagman said:**
> If it were me I'd borrow another drive from .. anywhere just to see if my drive was buggered.

btw... That's exactly what I had to do last week. When I removed my Sony DVDRW the sticker on top said 2003 so I guess I had a good run out of it.

It's not the hardware, as I said, I was able to boot off a live CD using the drive, and I've rechecked the connections just to make sure. Discs are recognised as the correct types when I insert them. The error messages I receive seem to indicate a permissions issue

> **gator2802 said:**
> If you can confirm that you have added the restricted drivers and your drive worked in 9.10 then you need to recheck that a driver was not blacklisted during the upgrade process.

The drive was working in 9.10, no restricted drivers for it were required at the time and none seem to be indicated now either, I don't know how to check to see if a drivers been blacklisted though

---

