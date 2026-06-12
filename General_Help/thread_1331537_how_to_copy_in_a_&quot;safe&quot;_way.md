---
title: "how to copy in a &quot;safe&quot; way"
date: 2009-11-19
forum: General Help
---

### Post by Depressure on 2009-11-19
Hi.

Backup is a nice thing, but I have just been looking through some of my pictures who has been copyed some times and the result is quite sad. some of my jpg's are really damaged. So how can I copy files from one drive to another safe? hash sum checking is one way around but can take some time, anybody got an idea?

---

### Post by whoop on 2009-11-19
> **Depressure said:**
> Hi.

Backup is a nice thing, but I have just been looking through some of my pictures who has been copyed some times and the result is quite sad. some of my jpg's are really damaged. So how can I copy files from one drive to another safe? hash sum checking is one way around but can take some time, anybody got an idea?

Copying files shouldn't change/damage the files at all. How are you copying files exactly?

---

### Post by MonoDeem on 2009-11-19
When you copy something, you do it byte-by-byte, which means, data shouldn't be corrupted in any way. What file systems have you used ?

---

### Post by prshah on 2009-11-19
> **Depressure said:**
> some of my pictures who has been copyed some times and the result is quite sad. some of my jpg's are really damaged. So how can I copy files from one drive to another safe? 

I suggest you can use rsync;

Salient points:
[indent]1) rsync will copy only files that either don't exist or need to be updated on the target
2) rsync will only copy the "bits" (nothing to do with bit/byte) of the files are are changed; eg, it will use a checksumming feature to figure out how to make the remote file "match" the current file. This will considerably speed up network transfers.
**3) rsync will _automatically_ (no need for special switches) check the destination file for "integrity" to ensure that the copy has occurred successfully.**
4) It can be used to transfer / archive / backup files either locally (same machine) or across the network.
[/indent]

That's the good part. The "bad" news is that both machines must have rsync installed and configured. It's very versatile, and by inference, complicated, but pretty simple to use if you do not want any advanced features.

There are too many options, so ```
man rsync
``` is the best place to start; or if you want to dive right in```
rsync -u * somemachine:somepath/
``` Replace machine names and paths as suitable, and look out for permissions!

---

### Post by Depressure on 2009-11-21
The thing is that I have copied from ntfs and ext3 and 4 (got some really old files) using cp and or copy mostly but some times (like in a hurry) gui.

rsync seems to do the bit yes and I will start to use it as soon as my server in the basement is ready, for now dropbox will do.

I think that the copying from my external usb drive to the pc has done much damage...

---

### Post by 3rdalbum on 2009-11-21
Digital data cannot be corrupted merely by copying from one device to another, unless one of the devices is faulty or the media (like CD) is faulty.

If those files were stored on CD-Rs at any point, this may be where the corruption started.

---

