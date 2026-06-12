---
title: "Where is my notes in the tomboy notebook is saved?"
date: 2009-07-21
forum: General Help
---

### Post by the-man-from-utopia on 2009-07-21
Hey! Recently my ubuntu jackalope distro stopped with automatic mounting, and I went in to etc/fstab to fix it manually. When I tried to reboot afterwards it came a lot of errors, I've obviously done something really wrong in there. But before I began changing the content in etc/fstab, I took a copy to a note in the notebook. (Yes I know it would have been much better to just save it as a plain text document, but its too late now) Now I have booted through a ubuntu intreprid idex live-CD, but I can't find my notes anywhere in my file system! So, does anyone know the path to where the notes is saved in the file system? 

Alternatively I could just simply reinstall the distro, but then I would loose all my files. Now I can see them through the live cd, but I have not permission to copy them to a usb-stick. If I try to, I get the error message: "the folder ".userPrefs" cannot be handled because you do not have permission to read it." Is it possible to somehow get this permission through the live CD so that I can copy all my files to a usb-stick?

Thanks in advance

---

### Post by plucky on 2009-07-21
> Where is my notes in the tomboy notebook is saved?

```
/home/<username>/.tomboy
``` <username>=your username

> Is it possible to somehow get this permission through the live CD so that I can copy all my files to a usb-stick?


Open a terminal and ```
gksudo nautilus
``` will open nautilus in sudo mode and should allow you to copy your files to a USB stick after the partition is mounted.

Good Luck

---

### Post by the-man-from-utopia on 2009-07-21
Splendid! Thanks! That did the job!:popcorn:

---

