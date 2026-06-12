---
title: "ntfs chkdsk no windows available"
date: 2010-02-05
forum: General Help
---

### Post by Icarus315 on 2010-02-05
I have a question but first here's my setup: No Windows, internal hard drive Ubuntu 9.10 ext4 only 1 partition and 1 swap partition.  USB external USB 2.0 hard drive 1 partition NTFS.  I've been using this setup for a while with Ubuntu just using NTFS-3g or FUSE or whatever it is to do the magic.  I would like to keep the USB drive NTFS because someday I may unplug it and bring it to a Windows machine.  Interoperability is fine on Linux, Windows machines not so much.  Anyway, today when I mounted it I was told it was dirty.  Bad drive, where you been?  Heh.  A bit of searching all pointed to booting into Windows to let it clean it.  Not going to happen, no Windows and I'm not about to go download some warez "live" disc to do so when needed.  So my question is, is there anyway to restore the dirty bit from within Linux only?  If Windows machines it may be plugged into some day supported other file systems it would be a non-issue but they don't so these are my constraints.  Thank you in advance for any advice.

---

### Post by cariboo on 2010-02-05
Install ntfsprogs from the repositories, there is a program called ntfsfix in the package.

---

### Post by Icarus315 on 2010-02-05
> **cariboo907 said:**
> Install ntfsprogs from the repositories, there is a program called ntfsfix in the package.

Thank you extremely much!!

---

### Post by zeroseven0183 on 2010-02-07
Hi! I have the same (almost the same, perhaps) issue and I'm trying this ntfsfix on a 250GB external USB had drive. But I get an error:

```
ntfsfix /dev/sdc1
Mounting volume... Error opening partition device: Permission denied.
Failed to startup volume: Permission denied.
FAILED
Attempting to correct errors... Error opening partition device: Permission denied.
FAILED
Failed to startup volume: Permission denied.
Volume is corrupt. You should run chkdsk.
```

I can't mount the hard drive and gives me this error message
> Error mounting: mount exited with exit code 13: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Failed to read first NTFS_BLOCK_SIZE bytes of potential restart page.
The file system wasn't safely closed on Windows. Fixing.
ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Failed to read NTFS $Bitmap: Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.
Failed to sync device /dev/sdb1: Input/output error
Failed to fsync device /dev/sdb1: Input/output error
Failed to close volume /dev/sdb1: Device or resource busy

From thread: [http://ubuntuforums.org/showthread.php?t=1309211](http://ubuntuforums.org/showthread.php?t=1309211)

---

### Post by Icarus315 on 2010-02-07
How I did it was to have the NTFS volume unmounted then call ntfsfix with the /dev/ naming while also running ntfsfix with sudo.  Are you using sudo to elevate it?  That could be the issue right there.

Edit: looking at the number of beans you have, well of course you are ;)  But still if its not in the code, must ask!

---

### Post by zeroseven0183 on 2010-02-08
Yes, I've tried that too but even if I use sudo with ntfsfix, I still get the same error. My friend doesn't want to wipe out the hard drive as it contains lot of data, her work and everything.

Although I'm thinking of doing that without her knowing then try recovering-- that's just to replace the bad clusters then mine the data afterwards.

Another thought that I have is that this could be a dead end for the hard drive, possibly mechanical.

---

### Post by NFblaze on 2010-02-08
Try downloading Hiren's Boot CD. I believe it has a program called MiniXP that boots up like a minimal LiveCD version of XP. I know from inside there you can access the command line, and maybe try running chkdsk from there. If that doesnt work it also, has some other tools on it that can attempt to help fix your hard drive.

---

