---
title: "Shared FAT32 Drive"
date: 2009-08-08
forum: General Help
---

### Post by fleamour on 2009-08-08
How do I navigate within Nautilus to drive F?  I have a FAT32 formatted drive for file sharing between Win2k & Xubuntu.  Can Xubuntu mount a NTFS drive?  I'm guessing not if it's hibernated.

---

### Post by michy99 on 2009-08-08
Unbuntu can mount an NTFS or FAT32 drive, It won't be recognized as the F: drive because linux does not use that system to name drives. Have a look at this page:

[http://maketecheasier.com/auto-mount-your-ntfs-partition-in-ubuntu/2009/04/14](http://maketecheasier.com/auto-mount-your-ntfs-partition-in-ubuntu/2009/04/14)

---

### Post by fleamour on 2009-08-09
I guess there is no need for a shared FAT32 drive after reading that.  I can always use it as a store drive though.  I have also installed a little app that lets Windows mount ext2 drives, ext3 drives being backwards compatible.  So if I need a file in either OS then should not be a problem!

Thanks.

---

### Post by fleamour on 2009-08-09
One thing, within Nautilus/Xubuntu there is no "Computer" tab to navigate sda 1-4.  I cannot seem to find an option to add remove such a function either?

---

### Post by fleamour on 2009-08-09
Actually it's Thunar file manager under Xubuntu & not Nautilus as in my Ubuntu guide.  Still cannot see a computer option.  Trawling the help files.

---

### Post by merlinus on 2009-08-09
Look in filesystem/media.

---

### Post by fleamour on 2009-08-17
> **merlinus said:**
> Look in filesystem/media.

This does not work for Jaunty?

EDIT:  My bad, auto mount with Storage Device Manager.

---

