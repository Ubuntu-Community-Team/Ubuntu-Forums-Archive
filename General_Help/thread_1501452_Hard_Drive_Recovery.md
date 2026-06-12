---
title: "Hard Drive Recovery"
date: 2010-06-04
forum: General Help
---

### Post by Is Mise on 2010-06-04
I recently hooked up an old IDE hard drive to my computer to transfer my old files off of it. After hooking it up and testing it in Ubuntu everything seemed to be fine, so I decided to back it up the following day. However, the the next day I booted up my Vista partition, and it started doing a disk check. It found a couple of file system errors and started to repair them, then an error message popped up saying something about being unable to write to the boot sector. After displaying this message, the computer froze up and had to be powered off.

Upon starting up the computer again, I found that Vista would no longer boot, and that Ubuntu would only boot after showing a black screen for about a minute. The Disk Utility program showed the old drive as having an unrecognized file system.

So I started up TestDisk to try to recover the partition, which found the missing partition after doing a Deep Search. All the files on the drive showed up correctly in the contents list, however when trying to write the changes to the drive, I got this message:

> fat32_boot_sector: Can't read boot sector.
Bad

Backup boot sector
OK

First sectors (Boot code and partition information) are not identical.
Second sectors (cluster information) are not identical.
Third sectors (Second part of boot code) are not identical.

Selecting Backup BS results in this error:

> Write error: Can't overwrite FAT32 boot sector

Rebuild BS also shows a similar error. So it seems like the boot sector of the drive is too damaged to fix, is there any way to copy the files found by TestDisk to a healthy hard drive? Any help is greatly appreciated.

---

### Post by Is Mise on 2010-06-04
Never mind, solved my own problem. I didn't notice the press "c" to copy option in the files list the first time.

---

