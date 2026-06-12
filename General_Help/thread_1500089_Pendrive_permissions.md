---
title: "Pendrive permissions"
date: 2010-06-02
forum: General Help
---

### Post by Pizarro on 2010-06-02
Having plugged a pen drive in to copy an office document for my wife to take to work I'm informed that I don't have permission.Right clicking on the drive tells me that permissions could not be determined. All I want to do is let my wife take her document to work and use it. How do I set the permissions? I can do it by using sudo nautilus and dragging but I'm sure I haven't needed to do this when using a pen drive before.

---

### Post by doas777 on 2010-06-02
what kind of filesystem does the pendrive have, and what os is installed on the work computer?

---

### Post by Pizarro on 2010-06-02
Fat32, Sadly windows at her work. Tried pen drive in my mac and can read and write to it. Seem to have same problem with my Usb hard drive now I've checked it. Think this may have started with system up grade to 10.04 or it may be coincidence.

---

### Post by doas777 on 2010-06-02
well, fat32 does not have any permissions so it must have something to do with the mounting process. if the problem is mounting, then it won't be  a problem in terms of mounting it on OSX. what user owns the mount point and what permissions does the mount point have?

---

### Post by Pizarro on 2010-06-05
Tells me owner is root when properties selected. Usb is part of an internal card reader. Identified as usb0. When plugged in it produces 2 entries in computer, 1 labelled USB DISK Pro: 2.0 GB Filesystem with pen drive icon, the other as usb0.

---

