---
title: "External ntfs hard drive fails to mount"
date: 2011-10-23
forum: General Help
---

### Post by shmibs on 2011-10-23
i have a 1tb hard drive which, up until recently, was functioning perfectly. however, just now it has spontaneously failed to mount. no messages whatsoever are being shown to me, and i have no idea what to do =/

the drive is spinning up properly when i plug in the usb 2.0 cable, but it is no longer being immediately recognised. after a few seconds, it starts to make a sound that, to me, sounds like it re-starting and trying to read from the beginning over and over. after a bit of that, the activity light will turn off and it will pause for a bit, then turn back on and repeat the process.

at first, lsusb does not list it as a detected device. after waiting for a while, however,
Bus 001 Device 021: ID 059b:0475 Iomega Corp. 
does show up. nothing changes, though...

i have no warranty and really don't want to lose all this data...
does it sound like a hardware issue that i should just give up on?

---

### Post by TeoBigusGeekus on 2011-10-23
Have you tried a different usb port?

---

### Post by shmibs on 2011-10-23
yes, i have.
Bus 002 Device 006: ID 059b:0475 Iomega Corp. 
with the same result

EDIT: this is a Samsung HD204UI, just in case extra data helps anything, and i'd love to have the drive just be usable, even if it requires a complete format or something.

---

### Post by TeoBigusGeekus on 2011-10-23
Can you post the output of
```
sudo fdisk -l
```
?

---

### Post by shmibs on 2011-10-23
```
WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00007049

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           1        2047+  ee  GPT
/dev/sda2   *           1       18693   150145024   83  Linux
/dev/sda3           18693       19458     6142976   82  Linux swap / Solaris

Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xee109927

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      243201  1953512001    7  HPFS/NTFS
```

---

### Post by TeoBigusGeekus on 2011-10-23
Try this:
```
sudo mkdir /media/m_point
sudo chown -R yourusername: /media/m_point
sudo mount /dev/sdb1 /media/m_point
```

---

### Post by shmibs on 2011-10-23
mount: special device /dev/sdb1 does not exist

---

### Post by TeoBigusGeekus on 2011-10-23
Damn!!!
Can you also post the output of
```
sudo parted /dev/sdb print
```
?

---

### Post by shmibs on 2011-10-23
it sat for a very LONG time and then output:
Model: SAMSUNG HD204UI (scsi)
Disk /dev/sdb: 2000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      32.3kB  2000GB  2000GB  primary  ntfs

why 2k GB? it was saying that earlier as well. i think something may be corrupted...

EDIT: running the same command a few seconds later returns that there is no such file or directory, so recognition is definitely flaky.

---

### Post by TeoBigusGeekus on 2011-10-23
I think you should plug your hd on a windows pc and run a checkdisk on it - it being an ntfs one.

---

### Post by shmibs on 2011-10-23
i tried that and, being windows, it froze up =/

---

