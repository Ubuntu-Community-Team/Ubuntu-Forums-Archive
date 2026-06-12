---
title: "Formatting with usb-booted Ubuntu"
date: 2012-01-02
forum: General Help
---

### Post by skeletine on 2012-01-02
Hi all,

All I want to do is format my hard drive, so I can install Windows I need, because that's the OS I need for all my music software. I installed new hardware, and now I need to format the hard drive. I booted Ubuntu from USB in order to back up my hard drive, and now I'm wondering if I can format the hard drive from there too.

If not, how can I go about formatting this drive? PREFERABLY using USB-booted things.

Cheers.

---

### Post by oldfred on 2012-01-02
You can use gparted in the Ubuntu liveCD/USB to create NTFS partitions.

If you create a primary NTFS partition with the boot flag then Windows will install to that.
Windows will  install to a blank drive, so it can create its NTFS primary partition(s), two for Windows 7. Or to a drive with unallocated space and primary partition(s) available.  If the unallocated space is not before the extended partition, it may have issues as Windows sometimes does not like extended partitions and writes a partition table that is invalid.

Some have reported that the NTFS partition created by gparted has to be reformated with the Windows repairCD/USB for Windows 7, but there have been no issues with gparted NTFS partitions and older versions of Windows. It may be related to the location on drive, before or after the extended partition.

---

