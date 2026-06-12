---
title: "How to access user files on live USB?"
date: 2009-11-20
forum: General Help
---

### Post by mma8x on 2009-11-20
i have a live installation on a usb drive.  is there any way to access my home files when the live system isn't booted? for example, i put the usb drive into my home computer and mount the fs.  the typical /home/user structure isn't there--so are my files inaccessible?  this would be of significance also if i choose to back up the usb.  i know i can boot up from the usb on the computer that i'm using, mount the HD, and copy that way.  likewise, i can use scp or similar.  both those options are kind of a PITA though.

---

### Post by emigrant on 2009-11-20
+1 looking for answer

---

### Post by bodhi.zazen on 2009-11-20
Yes, but not easily.

The file system is compressed using casper. So you can extract the file system and access your files from the extracted files.

See this link :

[https://help.ubuntu.com/community/LiveCDCustomization](https://help.ubuntu.com/community/LiveCDCustomization)

In the fires few sections at the top it explains how to extract the files, and if you edit them, at the bottom it explains how to replace (re compress the extracted files) the file system if you wish.

---

