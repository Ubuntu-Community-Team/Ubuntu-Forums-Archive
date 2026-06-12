---
title: "Unable to copy files"
date: 2010-11-19
forum: General Help
---

### Post by revhead347 on 2010-11-19
My computer doesn't like to copy files over 4 gigs to a flash drive.  It will copy for about 12 minutes, and then when it's almost done, it's says "File to large."  Is there some sort of limitation in the software that can be adjusted for this.

Thank you,
Kurt

---

### Post by SlugSlug on 2010-11-19
most likely your USB drive is FAT32 formatted -- this has a file size limit of around 3gig

you could format it ext4 or ntfs

---

### Post by revhead347 on 2010-11-19
> **SlugSlug said:**
> most likely your USB drive is FAT32 formatted -- this has a file size limit of around 3gig

you could format it ext4 or ntfs

Ok, awesome to know.  Can I reformat it using Xubuntu?  And if so, how do I do that?

Thanks for your help.
Kurt

---

### Post by SlugSlug on 2010-11-19
open a terminal 
unplug usb

ls /dev/sd*

this will list some devices

plug usb in  wait 10 secs
ls /dev/sd*

this will now list an additions device (usb)  lets say it listed /dev/sdc

sudo mkfs.ext4 /dev/sdc1


will format it ext4  !! will wipe everything thats on sdc1 !!

---

### Post by endotherm on 2010-11-19
plug it in, and then open System -> Administration -> disk Utility. just click format. 
be sure to move any data you would like to keep, before formatting.

---

### Post by revhead347 on 2010-11-19
Ok, instead of going to disk utility, I went to GParted, which I think would be the same thing as disk utility for Xubuntu.  On the menu, there is a scroll out listing for "format >".  It is an inaccesible function.  Next to the device listing, there is a set of keys.  I assume this means that somehow this device has become locked, and that's why it won't let me format it.  Any ideas on how to unlock it?

Kurt

---

### Post by WorMzy on 2010-11-19
When you plugged it in, it was, most likely, automatically mounted. Unmount it (in any way - file manager or "umount" or from inside gparted), and you should be able to format it.

---

### Post by SlugSlug on 2010-11-19
close gparted

open a terminal and try

gksudo gparted

---

### Post by revhead347 on 2010-11-19
Thanks a bunch guys.  I got it to work without opening up a terminal.  The first time I went ext4, the computer froze.  It worked the second time, and then I realized that Windows didn't like the ext4 format.  I reformatted in ntfs, and it works great.  I have to get these files onto the only Vista computer in the house, because it has the only working DVD burner.  I would buy a DVD burner for this computer, but I can't even get the CD burner I have on it to work, so I don't want to spend the money.

Kurt

---

