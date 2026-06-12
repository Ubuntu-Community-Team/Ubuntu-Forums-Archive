---
title: "PSPgo mounts with glitchy name, mount point stays in /media after unplugged"
date: 2010-02-23
forum: General Help
---

### Post by Dirjel on 2010-02-23
Beginning a few days ago, whenever I plug in my PSPgo via USB, it shows up in Nautilus as:
```
SONY "PSP" SS: 1C[and then a glitchy square thing, see screenshot].
SONY "PSP" MS: 16 GB Filesystem
```

The first line is the system's onboard memory, and the second line is my 16 gig memory card.  It used to mount as:
```
SONY "PSP" SS: 16 GB Filesystem
SONY "PSP" MS: 16 GB Filesystem
```

I *cannot* unmount the drive.  The computer does not seem to be able to find the mount point to take it off from.  When I unmount from Nautilus, it says:
```
Unable to unmount location

Error unmounting: umount exited with exit code 1: umount: /media/1C: not found
```
If I just unplug the drive, the entry in /media remains as 1C[glitchy box thing][series of underscores] (see screenshot)

I tried looking at the drive in gparted, and it says:
```
Unable to find mount point

Unable to read the contents of this file system!
Because of this some operations may be unavailable.
```
The disk has the label
```
1C^LM-^SM-^P^KHM-^?M-^?M-cM-A
```

Any idea how to fix it?  Is my PSPgo becoming corrupt or something?  That would be supremely unpleasant.  I'd definitely like to avoid that, if at all possible.  Any help would be greatly appreciated, thanks.

---

### Post by Dirjel on 2010-02-28
...Help?

---

### Post by Dirjel on 2010-03-05
Alright, so I plugged the drive into my little brother's computer (also running Ubuntu), and it had the same behavior.

I tried plugging it into my mother's computer (running Windows XP), and it behaved as it should.  That is, it mounted as "Drive F:" and when I right click > Properties'd it, it said that it was a Sony "PSP" SS: 16 GB Filesystem.

Looks to me like it's a Linux problem, and not a problem with my PSP.

---

### Post by Dirjel on 2010-03-09
Bump~

It hasn't fixed itself, and my "Places" menu is getting crowded >.>

---

### Post by Chronon on 2010-03-09
I don't really know anything about this device, but it sounds like it mounts as a UMS device.  You might try scanning the file system and see if you can detect and fix any errors.

---

### Post by Dirjel on 2010-03-09
Yeah, it mounts as a regular USB drive.

I have no idea how to go about "scanning the file system and seeing if I can detect and fix any errors."  I cannot access it via the command line at all, and gparted seems to be only dimly aware that the thing exists.  I genuinely have no idea at all how Nautilus is able to see it.

---

### Post by Chronon on 2010-03-12
It definitely strikes me as a badly corrupted file system.  If you can figure out which partition on which device is the one that gets mounted in UMS mode, then you could use fsck to try to repair it.  (fsck shouldn't be run on a mounted partition anyway.)

This page has a good description, or you can just consult the manpage.
[http://www.computerhope.com/unix/fsck.htm](http://www.computerhope.com/unix/fsck.htm)

You might want to use fsck.vfat if the partition is formatted as FAT32.

Try running dmesg after plugging in the device to figure out which partition is trying to be mounted.

---

### Post by Dirjel on 2010-03-13
Alright, fsck did a whole lot of nothing, near as I can tell.  However, it did get me started on the right track.  I looked through the manpages of that and a few other related programs, and was able to figure out the device name of my PSP.  From there, I was able to unmount it via command line (using /dev/sdj1 instead of /media/1C[glitchy square]), then finally I was able to access it via gparted.

Gparted was able to fix it.

Thanks for the help, Chronon.  You're the man.

---

