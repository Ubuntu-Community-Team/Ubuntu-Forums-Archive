---
title: "HOWTO: Changing USB or hard drive mount point (Rename drive)"
date: 2010-03-14
forum: General Help
---

### Post by Francewhoa on 2010-03-14
**Requirements**
-Ubuntu 8.04.x the Hardy Heron. LTS Desktop edition.

**Steps**
-Insert your USB stick or if not already done mount your HD. Wait a few secondes.

-Navigate to 'Places'. When your drive appears, left click on it. Some time USB sticks don't mount automatically this should fix it by displaying it on your desktop.

-Go to your desktop. Right click the newly mounted drive. Select Properties option.

-Navigate to Volume tab > Select 'Settings' drop down menu.

-In 'mount point' field, type the name you want to call it. Don't type /media/ though. For example
    usbdisk
    or
    harddrive2

-Close

-Right click > Unmount

-If your drive is a USB stick remove and reinsert it. If your drive is a hard drive navigate to 'Places' then select your hard drive. This will mount it.

-Your drive should now be called usbdisk, and be located at /media/usbdisk. The mount point will change but the label won't. In other words in this example all files will be located at harddrive2/bla/bla but the volume label on the desktop will show as '500 GB Media'.

---

