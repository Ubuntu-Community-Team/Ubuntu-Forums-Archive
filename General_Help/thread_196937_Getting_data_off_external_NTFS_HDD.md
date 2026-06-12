---
title: "Getting data off external NTFS HDD"
date: 2006-06-15
forum: General Help
---

### Post by Cable on 2006-06-15
I have some backup data (from before installing Dapper) that I need to get off of my external HDD.  It's formatted with NTFS (which is fine, I just need to be able to read it).  First off, it's firewire.  Will this work?  If so...

How do I mount the drive (it has at least two partitions), get the data off, then unmount it *without* ruining it?  It has other important stuff on there that cannot be lost.

Help is greatly appreciated!  Thanks!

---

### Post by c-prompt on 2006-06-15
I have an external WD HDD that has firewire (and usb).  It automounts in dapper read-only just fine.  All I do is plug it in, and the HDD shows up on the desktop.  Its mount-point is somewhere in /media.

---

### Post by Cable on 2006-06-15
When disconnecting it from the computer, do I need to unmount *then* unplug, or can I safely just unplug it?

---

### Post by xwipeoutx on 2006-06-15
You'd do best to unmount it...

You should be able to unmount it by right-clicking the icon on your desktop (much like you unmount a usb key)

---

### Post by RAOF on 2006-06-15
For read-only, you can **probably** just safely unplug it.  But it's a **very** good idea to be in the habit of unmounting/ejecting removable media before disconnecting.

---

