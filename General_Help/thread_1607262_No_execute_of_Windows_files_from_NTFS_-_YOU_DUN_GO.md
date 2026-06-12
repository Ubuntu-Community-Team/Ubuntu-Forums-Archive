---
title: "No execute of Windows files from NTFS - YOU DUN GOOFED!"
date: 2010-10-27
forum: General Help
---

### Post by darksoul7 on 2010-10-27
So I have an NTFS volume with many programs I (used to) use on a regular basis. Since upgrading to 10.10, I can't use them. Obviously, an execute bit cannot be added onto files on an NTFS volume. These are Windows programs that ran perfectly with WINE on 10.04. 

I have tried ```
mount -o remount,exec /media/0A08B33E08B32819
```

It doesn't work. I do not have the luxury of installing PlayOnLinux to do the script workaround. The programs are too large to move to the EXT4 volume I have set up for Linux.

I need a work around on this ASAP or I'm ditching Ubuntu for good. From the stupid "let's make the buttons on the left like Mac" (which I have switched back over, but it's still annoying) in Lucid to this glorious fail in Maverick, Debian is looking better and better. Besides, it's not like the packages installed in Ubuntu can't be installed in other distros.

Yes, I'm rather PO'ed. This is a major loss of productivity for me.

---

### Post by WorMzy on 2010-10-27
> mount -o remount,exec /media/0A08B33E08B32819

Is there an entry for /media/0A08B33E08B32819 in fstab? If not, then you're missing an argument here - the device identifier. If you do have an fstab entry for it, post it here.

---

### Post by Morbius1 on 2010-10-27
Internal ntfs partition or external?

---

### Post by darksoul7 on 2010-10-27
@Wormzy - 0A08B33E08B32819 is the "name" of the drive.

@Morbius1 - it's an NTFS partition on the same physical disk.

---

### Post by Morbius1 on 2010-10-27
You have control over how the partition is mounted if it's an internal disk.

First, create a permanent home for the partition to live in ( this is just an example ):
```
sudo mkdir /media/Data
```Then add a line to your fstab that looks like this:
```
UUID=0A08B33E08B32819 /media/Data ntfs defaults 0 0
```Check for errors and mount the new partition:
```
sudo mount -a
```BTW I'm guessing that the UUID of that disk is in fact 0A08B33E08B32819.

To verify you can run the following command:
```
sudo blkid -c /dev/null
```In the defaults is a "umask=000" parameter which will make all folders and directories have permissions of 777 - execute bit turned on.

---

### Post by darksoul7 on 2010-10-27
@Morbius

I kneel to your Linux superiority! ALL HAIL MORBIUS!!!


Thanks, now I can actually get some work done! :D

---

