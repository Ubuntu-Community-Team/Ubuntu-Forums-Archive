---
title: "Need help with unreadable WD MyBook terrabyte drive on Ubuntu 10.04 LTS"
date: 2010-05-08
forum: General Help
---

### Post by jazzhead on 2010-05-08
Hello all,

I've been using a WD MyBook terrabyte USB drive for several months with no problem. Several days ago, I used the "safely remove drive" option but then unplugged the cable before the removal process had finished.

Now when I plug the drive in, the WD SmartWave section of the drive will mount. This is additional software for Windows computers that came with the drive and that I don't use. The main drive itself, though, will not mount. The drive doesn't show up on the left side of a navigation window, either.

I can see the drive using Disk Utility. It is located at /dev/sbd. 

Can anyone help me (a) mount this drive or (b) recover its data so I can format it? I'd much prefer (a), of course. 

Regarding my level of tech savvy: I've been using Ubuntu for a couple years, but I chose Ubuntu because it allows me to use Linux while still remaining relatively ignorant about things, which is my comfort zone.

Thanks in advance for any help you can provide.

All the best,

Jason

---

### Post by srs5694 on 2010-05-08
It sounds like you left the default partitions and filesystems in place. If so, the disk probably uses NTFS, and Linux has very poor filesystem check tools for NTFS. If I'm right that the disk uses NTFS, then AFAIK your only choice is to plug the disk into a Windows computer to have it check the disk. (This should probably occur automatically, but you can manually tell Windows to check the disk, if necessary.)

If you only use the disk from Linux, then after you do this check, I recommend you copy the data off the drive and create a new Linux-native filesystem (such as ext3fs or XFS) on the disk, so that you'll be able to perform disk checks in Linux. You can then copy your data back to the disk.

---

