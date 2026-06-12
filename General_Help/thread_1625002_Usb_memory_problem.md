---
title: "Usb memory problem"
date: 2010-11-18
forum: General Help
---

### Post by steffenomak on 2010-11-18
I had a usb memory stick that was used for general storage, but the problem was that I installed Ubuntu 10.10 beta on my laptop and plugged in the memory stick, and now windows or ubuntu wont see the stick at all. Was wondering if I fried it somehow? And if it is true, wtf?

Thx for the help

---

### Post by Mark Phelps on 2010-11-18
I'm presuming this USB stick came preformatted and you used it to copy files back and forth, right?

In that case, it was probably formatted as FAT (or maybe, FAT32) -- and if you simply pulled it out of your Ubuntu machine, without doing Safe Removal, that could have left the filesystem in a corrupted state.

IF you have an MS Windows machine, see if you can run chkdsk on the USB stick.  IF you can't, it's likely hosed.

---

### Post by steffenomak on 2010-11-18
> **Mark Phelps said:**
> I'm presuming this USB stick came preformatted and you used it to copy files back and forth, right?

In that case, it was probably formatted as FAT (or maybe, FAT32) -- and if you simply pulled it out of your Ubuntu machine, without doing Safe Removal, that could have left the filesystem in a corrupted state.

IF you have an MS Windows machine, see if you can run chkdsk on the USB stick.  IF you can't, it's likely hosed.

Ok, but the thing is that it happened when it was plugged in. Or I just transfered everything and took it out, but gonna check and see

---

