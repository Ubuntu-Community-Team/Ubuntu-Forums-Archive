---
title: "unmountable ntfs hard drive"
date: 2010-05-03
forum: General Help
---

### Post by supermooshman on 2010-05-03
Hi all,

I just tried mounting my Iomega 1tb hard external hard drive, but it doesn't seem to work. The drive doesn't show up in nautilus. When I look at it with parted it shows as a ms-dos filesystem. If I plug it into my imac, it shows doesn't mount either, but in the driveutility it shows up as a fat32.
Windows 7 doesn't seem to helpfull as it just says that the drive needs to be formatted.

Is there any way to recover my files before I format, or better yet solve this problem without formatting?

thanks

---

### Post by dino99 on 2010-05-03
need to check if its a iomega hardware problem or not (look logs)

install, if not : usbmount mountmanager (set prefs)

need: ntfsprogs, ntfs-3g to be installed

into synaptic, jazip is a special iomega package, maybe try it

---

### Post by supermooshman on 2010-05-03
> **dino99 said:**
> need to check if its a iomega hardware problem or not (look logs)

install, if not : usbmount mountmanager (set prefs)

need: ntfsprogs, ntfs-3g to be installed

can you just quickly remind me how to go about this (especially the logs thing)

---

### Post by dino99 on 2010-05-03
> **supermooshman said:**
> can you just quickly remind me how to go about this (especially the logs thing)
system - admin - synaptic ( to install packages)
system - admin - log viewer (for logs)

---

### Post by supermooshman on 2010-05-03
> **dino99 said:**
> 
system - admin - log viewer (for logs)
ok thanks, is there anything special I should look for in the logs?

---

### Post by supermooshman on 2010-05-03
anyone? 
I have had a look at the logs and... well, to me it is all gibberish...

---

