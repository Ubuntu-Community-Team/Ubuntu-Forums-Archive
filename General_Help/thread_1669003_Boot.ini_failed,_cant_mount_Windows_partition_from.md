---
title: "Boot.ini failed, cant mount Windows partition from live usb"
date: 2011-01-17
forum: General Help
---

### Post by cbob on 2011-01-17
Hi,
The boot.ini file for windows fail(reason unknown) and now i cant boot  to any installed OS. Used Ubuntu live from usb to explore the disks, but  as i tried to mount the Wíndows partition it failed..
```
# mount -t ntfs-3g /dev/sda /media/c/
ntfs_mst_post_read_fixup: magic: 0xffffffff  size: 1024  usa_ofs: 65535   usa_count: 65534: Invalid argument
Record 0 has no FILE magic (0xffffffff)
Failed to load $MFT: Input/output error
Failed to mount '/dev/sda': Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.

```I wish to run the 'chkdsk \f' in windows but must fix the  boot.ini file first to be able to enter it.. 
Really at a loss here, how can i mount the windows partition?
```
# fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x2052474d

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   ?         410      119791   958924038+  12  Compaq  diagnostics
Partition 1 does not end on cylinder boundary.
/dev/sda2   ?      121585      234786   909287957+  43  Unknown
Partition 2 does not end on cylinder boundary.
/dev/sda3   ?       14052       14052           5   72  Unknown
Partition 3 does not end on cylinder boundary.
/dev/sda4          164483      164486       25945    0  Empty
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order

Disk /dev/sdc: 4009 MB, 4009754624 bytes
145 heads, 48 sectors/track, 1125 cylinders
Units = cylinders of 6960 * 512 = 3563520 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc3072e18

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        1126     3915752    c  W95 FAT32 (LBA)

Disk /dev/sdb: 2011 MB, 2011168768 bytes
128 heads, 32 sectors/track, 959 cylinders
Units = cylinders of 4096 * 512 = 2097152 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         958     1961152+   6  FAT16

```Regards,
cbob

---

### Post by mikewhatever on 2011-01-17
> **cbob said:**
> 
I wish to run the 'chkdsk \f' in windows but must fix the  boot.ini file first to be able to enter it.. 
Really at a loss here, how can i mount the windows partition?


Mounting a corrupted file system is a bad idea, as it can corrupt the file system even further. Get a Windows recovery tool and use that to check the file system.

---

### Post by cbob on 2011-01-17
Have any suggestions on such a tool?

---

### Post by mikewhatever on 2011-01-17
You Windows installation disk should have a recovery console mode, from which you should be able to run the suggested chkdsk /f command. If you don't have the disk, search for recovery disk in conjunction with your version of Windows.

---

### Post by cbob on 2011-01-25
Thanks for your relays! 
A frustrating week later,
Have not been able to access the Window recovery tool. This due to the fact i have no cd unit and no Window XP computer nearby to make a usb-boot:er.
Any Windows recovery tool that is downloadable and usable from usb?

---

### Post by Mark Phelps on 2011-01-25
By "windows recovery tool", I think they meant Windows Recovery Console -- which you can get to by pressing F8 when you boot.  But that's only true if you took the extra step to install WRC when you installed XP.  It's not installed by default.

I've read that Hiren's Boot CD contains chkdsk and other tools.  You should go their homepage because that has links for creating a boot USB.  After you have that created, you could add the utilities from Hiren's Boot CD to that USB stick.

---

### Post by cbob on 2011-02-12
Late hello,
I've would not call the thread solved but it no longer a problem. Clean Ubuntu install solved all windows problems:)
Thanks anyway! And Hiren's Boot was packed with usable tools, couldn't fix the problem anyway..

regards,
cbob

---

