---
title: "Convert filesystem back to ntsc"
date: 2010-07-07
forum: General Help
---

### Post by zonedabone on 2010-07-07
Ok. I installed linux on an external hard drive, and now I want to use the drive for storing video files on windows. Sadly, when I insert it while running windows, windows doesn't recognize the drive in the my computer screen, and I think it's because it's in ext3/ext4 format. I want to convert it to ntsc format, and I don't care about any of the files on it. What's the easiest way for me to SAFELY convert it to ntsc, with no risk of damagin the hardware or messing up my HD contents. I'm running ubuntu off of the live disk.

Thanks in advance!

---

### Post by zonedabone on 2010-07-07
ALso, somehow it says that I don't own it.

---

### Post by btindie on 2010-07-07
**NTSC** is the TV standard used in North America, you mean **NTFS**.
 
Plug the disk in when booted in Windows then type *diskmgmt.msc* at the command prompt. Delete the existing partition then create a new NTFS one.
 
Doesn't really have anything to do with Linux.

---

### Post by Seanlol on 2010-07-07
> **zonedabone said:**
> Ok. I installed linux on an external hard drive, and now I want to use the drive for storing video files on windows. Sadly, when I insert it while running windows, windows doesn't recognize the drive in the my computer screen, and I think it's because it's in ext3/ext4 format. I want to convert it to ntsc format, and I don't care about any of the files on it. What's the easiest way for me to SAFELY convert it to ntsc, with no risk of damagin the hardware or messing up my HD contents. I'm running ubuntu off of the live disk.

Thanks in advance!

If you're in a Live CD, open GParted, delete the ext4 partition and format it as NTFS.

---

### Post by zonedabone on 2010-07-07
Ok. The file system has been successfully converted to NT_FS_;) so the problem is pretty much solved. There's only one thing. When I used the Disk Management Utility, it made it so that the EXTERNAL drive is categorized as a hard disk. Does windows treat these differently, such as making it more permanent? I'd like to be able to unplug it and replug it in. Should I change it to be a device with removable storage, and if so, how?

---

### Post by btindie on 2010-07-07
That's how Windows treats external hard disks, something to do with how the USB device presents itself to the USB host adapter. Other than that it really is a Windows question...

---

### Post by zonedabone on 2010-07-07
Ok. I thought it started as a windows question, but it has now become a windows question, and has been solved, so I think I will put the wonderful tag on this thread and give another big thank-you to the Ubuntu Community!

Now, time to go watch a movie on the drive!:popcorn:

---

