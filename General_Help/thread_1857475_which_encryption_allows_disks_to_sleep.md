---
title: "which encryption allows disks to sleep?"
date: 2011-10-10
forum: General Help
---

### Post by alfonso78 on 2011-10-10
Hi,

I'd like my RAID6 array to be encrypted and I thought about several options to encrypt the whole RAID partition:

- TrueCrypt
- Scramdisk 4 Linux (SD4L)
- dm-crypt + LUKS

After reading few posts about it I decided to put JFS on top of the encryption.

Just to clarify: this is NOT the OS disk, and the OS runs on a separate disks with no RAID and no encryption. Also there is no multiboot.

In order to choose my favorite solution I have these two requirements:

- a system that I can access also from a standard bootable ubuntu usb stick (for this purpose it seems rescue RAID is simple ([http://blog.tcg.com/tcg/2006/04/recovering_raid.html](http://blog.tcg.com/tcg/2006/04/recovering_raid.html)) and rescue LUKS also ([http://www.ubuntugeek.com/rescue-an-encrypted-luks-lvm-volume.html](http://www.ubuntugeek.com/rescue-an-encrypted-luks-lvm-volume.html))

- a system which is capable to unmount the disks (meaning I need to retype the password) and put them to sleep after a certain time has elapsed.

As far I understand, TrueCrypt doesn't offer that option under Linux (auto un-mount is only available on Windows) - according to [http://ubuntuforums.org/showthread.php?t=1567703](http://ubuntuforums.org/showthread.php?t=1567703)

SD4L reads also TrueCrypt volumes (see [http://sourceforge.net/project/screenshots.php?group_id=101952&ssid=103722](http://sourceforge.net/project/screenshots.php?group_id=101952&ssid=103722))

What about dm-crypt / LUKS? Do you know if auto-unmount is possible?

Any other consideration based on your experience?

thank you!

---

