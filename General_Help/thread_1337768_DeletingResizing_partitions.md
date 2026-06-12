---
title: "Deleting/Resizing partitions"
date: 2009-11-25
forum: General Help
---

### Post by olympic on 2009-11-25
I am in the process of deleting WinXP from my hard drive and have a query concerning re-using the freed up space.

My drive is currently configured as follows:

/dev/hda1     ntfs  (WinXP)    49.96Gb    
/dev/hda2     Extended         99.09Gb
/dev/hda5     Ext3  (/)        18.63Gb
/dev/hda6     Swap              3.72Gb
/dev/hda7     Ext3  (Usr)      76.73Gb

Question:  If I delete the WinXP partition using Gparted, can I then just resize /dev/hda5 to take up the free space and will I have any problems when I reboot?  I would like to have the 49.96Gb space available in hda5 if possible.

I am on an ACER Aspire 3634 laptop.

Thanks in advance

---

### Post by audiomick on 2009-11-25
If you just re-format the windows partition as ext3, you can then mount it into your Ubuntu file system. That is the safest thing to do. Changing partition size works pretty well, but there is always a small risk.
I would be inclined to just do as I said for now. Time will come when you want to re-install, then you can "tidy up"

---

