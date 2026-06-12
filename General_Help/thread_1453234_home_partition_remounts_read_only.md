---
title: "/home partition remounts read only"
date: 2010-04-13
forum: General Help
---

### Post by jjacobs2 on 2010-04-13
Hi,
I have a separate home partition setup with root on one drive and /home on the other.  After using the computer for awhile the /home partition will remount itself as read only.  Fsck did not find any errors and reformatting did not fix the problem.  Rebooting makes the partition work normally for awhile but the problem comes back eventually.  SMART testing did not find any problems with the hard drive.  (It's a seagate so that may not be accurate.)  Any ideas what the problem could be and how to fix it?

---

### Post by dcstar on 2010-04-13
> **jjacobs2 said:**
> Hi,
I have a separate home partition setup with root on one drive and /home on the other.  After using the computer for awhile the /home partition will remount itself as read only.  Fsck did not find any errors and reformatting did not fix the problem.  Rebooting makes the partition work normally for awhile but the problem comes back eventually.  SMART testing did not find any problems with the hard drive.  (It's a seagate so that may not be accurate.)  Any ideas what the problem could be and how to fix it?

It is an internal drive?

---

### Post by TitanusEramius on 2010-04-13
If I should guess I would say that you are using the wrong mount-options for /home.

Could you please post the content of /etc/fstab?
You can use both "cat /etc/fstab" & "gedit /etc/fstab" in the terminal to do this.

---

### Post by jjacobs2 on 2010-04-13
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb1 during installation
UUID=5bae8286-7c7e-4850-b2bd-13d1360d73d5 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda1 during installation
UUID=808fa388-b1cf-494e-a289-ecbeded3f8e5 /home           ext4    defaults        0       2

Both drives are internal.  All of the options in fstab were set by default by ubiquity.

---

### Post by jjacobs2 on 2010-04-14
I was looking through the logs and noticed errors related to the home partition encryption.  
 ecryptfs_write_end: Error encrypting page (upper index [0x00000000000009a2])
This error repeats many times.  Is there a restriction on encrypted home partitions being on separate directories?

---

### Post by jjacobs2 on 2010-04-14
Scanning 1 areas for low memory corruption
Apr 13 02:41:47 Terra kernel: [    0.000000] modified physical RAM map:
Apr 13 02:41:47 Terra kernel: [    0.000000]  modified: 0000000000000000 - 0000000000001000 (usable)
Apr 13 02:41:47 Terra kernel: [    0.000000]  modified: 0000000000001000 - 0000000000006000 (reserved)
Apr 13 02:41:47 Terra kernel: [    0.000000]  modified: 0000000000006000 - 0000000000098800 (usable)
Apr 13 02:41:47 Terra kernel: [    0.000000]  modified: 000000000009f800 - 00000000000a0000 (reserved)
Apr 13 02:41:47 Terra kernel: [    0.000000]  modified: 00000000000f0000 - 0000000000100000 (reserved)
Apr 13 02:41:47 Terra kernel: [    0.000000]  modified: 0000000000100000 - 00000000cfde0000 (usable)
Apr 13 02:41:47 Terra kernel: [    0.000000]  modified: 00000000cfde0000 - 00000000cfde3000 (ACPI NVS)
Apr 13 02:41:47 Terra kernel: [    0.000000]  modified: 00000000cfde3000 - 00000000cfdf0000 (ACPI data)
Apr 13 02:41:47 Terra kernel: [    0.000000]  modified: 00000000cfdf0000 - 00000000cfe00000 (reserved)
Apr 13 02:41:47 Terra kernel: [    0.000000]  modified: 00000000e0000000 - 00000000f0000000 (reserved)
Apr 13 02:41:47 Terra kernel: [    0.000000]  modified: 00000000fec00000 - 0000000100000000 (reserved)
Apr 13 02:41:47 Terra kernel: [    0.000000]  modified: 0000000100000000 - 0000000130000000 (usable)
Apr 13 02:41:47 Terra kernel: [    0.000000] Using GB pages for direct mapping
Apr 13 02:41:47 Terra kernel: [    0.000000] init_memory_mapping: 0000000000000000-00000000cfde0000
Apr 13 02:41:47 Terra kernel: [    0.000000] NX (Execute Disable) protection: active
Apr 13 02:41:47 Terra kernel: [    0.000000] init_memory_mapping: 0000000100000000-0000000130000000
Apr 13 02:41:47 Terra kernel: [    0.000000] NX (Execute Disable) protection: active
Is it normal to scan for corruption or perhaps the memory is corrupt?

---

