---
title: "Trying to mount Sansa E260 portable media player"
date: 2009-07-16
forum: General Help
---

### Post by Bucky Ball on 2009-07-16
Hi all,

The name of the thread kinda says it. The Sansa E260 is using /dev/sdc, which I discovered with:

```
sudo blkid
```It doesn't auto-mount but the player itself shows it is connected and is even charging. I worked out how to get to it - dropped some songs on, unplugged but they don't seem to be there - by using this command:

```
sudo mount -t vfat /dev/sdc /media/Sansa
```... on the fly, but when I tried to make it so I would mount when I plugged in, I added it to fstab like this:

```
/dev/sdc    /media/Sansa    vfat    rw,user,noauto,exec    0    0
```No joy. Plug in and nothing. But it still shows in result of 'sudo blkid' and also following this path to this directory:

```
/dev/disk/by-id
```... in which I find these two files (but there is only one E260; could this be the confusion?):

```
usb-SanDisk_Sansa_e260_340BEC183804B5940000000000000000-0:0
usb-SanDisk_Sansa_e260_340BEC183804B5940000000000000000-0:1
```When I try it with the 'on the fly' command again it mounts straight up, no problem. Hmm. Trying to fix this for the in-laws while I'm here for a few days, so any suggestions gratefully appreciated. :)

(ps: I recently bought a Linux-friendly Cowon iAudio 7 and this is kinda making me glad I did: when that arrived I plugged it in, an an 'iAudio 7' icon appeared and I was dragging and dropping files onto it immediately ... and it is a sweet gizmo sound-wise).

---

### Post by Bucky Ball on 2009-07-16
bump

---

### Post by Chronon on 2009-07-17
Read this bug report: [https://bugs.launchpad.net/ubuntu/+source/libgphoto2/+bug/355998](https://bugs.launchpad.net/ubuntu/+source/libgphoto2/+bug/355998)

It seems to be the source of similar trouble for people.  I'm not sure what's the difference between "Fix released" and "Fix committed".  I guess this means the bugfix could be pushed out to the repositories soon.  Otherwise you can try one of the workarounds posted in that bug report.

---

### Post by Bucky Ball on 2009-07-17
Thanks for that. I actually found that page last night and "Followed these simple instructions" from that page but to no avail. Proceedings stopped when I was asked what file to patch. I had no idea but tried a few to no result.

I will tinker more when I am back at that computer. We are in Melbourne for a couple of days then back there for another couple so fingers crossed I can discover some fix or workaround.

Cheers. :)

---

### Post by Bucky Ball on 2009-07-19
This is in the result of 'sudo blkid' when I plug in the sansa E260:

```
Bus 001 Device 004: ID 0781:7422 SanDisk Corp.
```

Nothing yet. Trying to mount through fstab.

---

### Post by Bucky Ball on 2009-07-19
Okay, I can mount it, only when I boot up with the unit plugged in and switched on, using this command after having set up the appropriate mount point and checked where the Sansa is being recognised:

sudo mount -t vfat /dev/sdc /media/Sansa

Works a treat, but I have no permissions (can't drop any files in there or delete any) unless of course I use Nautilus.

Any ideas as to what I could put in /fstab to mount it with full permissions at boot?

Also, the Sansa is showing as having 3.4Gb used space (it is 4Gb). Weird as there is nothing on it except a few empty folders.

---

### Post by Bucky Ball on 2009-07-19
bump (I leave tomorrow so sorry for bumping but running out of time).

I can mount it if plugged in at boot, with no permissions and a lot of stuffing about. Of no use to the inexperienced OPs that own the machine. 

There must be some way of translating:
```

sudo mount -t vfat /dev/sdc /media/Sansa
```... and line in /etc/fstab that will mount the drive with permissions. Surely??? That line works fine except for permission. Could I even write a script and make an icon to boot it (with permissions)?

---

### Post by Bucky Ball on 2009-07-20
Success! About all I remember is last thing before bed at some un-Godly hour, going to Settings->Format on the Sansa E260 and formatting (had nothing on theortically anyhow, even though telling me 3.7Gb used).

Switched on the machine today, plugged in E260 and there it was, booted automagically as '4.1Gb Media' or something of the like, and read and write permissions fine! It now shows 3.7Gb FREE, not used as before.

Must have shaken something loose with my fumblings. :)

---

