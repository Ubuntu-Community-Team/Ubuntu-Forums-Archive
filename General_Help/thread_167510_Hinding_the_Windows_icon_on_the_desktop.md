---
title: "Hinding the Windows icon on the desktop"
date: 2006-04-28
forum: General Help
---

### Post by Hoffmann on 2006-04-28
Hi,

I have mount my Windows NTFS partition on Ubuntu 5.10 successfully. So, I have access to my Windows XP partition from Ubuntu, and all is working fine. Just one thing have 'bored' me. I would like to hind the Windows icon that appears on the desktop. It seems like I would like to 'forget' Windows when I am using Linux. :-D 

Is there a way to hind that icon from the desktop?

Thanks!
Hoffmann

---

### Post by sinkxdie on 2006-04-28
I have that same problem so *bump*
I really wish someone would help...because all my music is on my NTFS drive and I don't want to keep mounting and unmounting it.

---

### Post by Nano Geek on 2006-04-28
In the terminal type:
```
gconf-editor
```Then, in the left hand menu, go: **apps**, **nautilus**, **desktop**, and uncheck **volumes_visible**. That should fix it.

---

### Post by sinkxdie on 2006-04-28
Thanks...
And haha its like the registry for Windows. :D

---

### Post by Hoffmann on 2006-04-28
[QUOTE=sinkxdie]I have that same problem so *bump*
I really wish someone would help...because all my music is on my NTFS drive and I don't want to keep mounting and unmounting it.[/QUOTE]

sinkxdie:

Actually, I have my NTFS mounted all the time. What I want is just to hind that icon, if possible.
Ok. In order to have your NFTS partition mounted all the time do the following:

(1) Create a directory to attach (mount) your windows file system:

sudo mkdir /Windows

(2) In order to have your NTFS mounted on automatically each boot-up:
Assuming that /dev/hda1 is the location of your Windows partition (NTFS)
Remember, you created the directory: /Windows

sudo gedit /etc/fstab, and add the following line to that file:

/dev/hda1       /Windows  ntfs    nls=utf8,umask=0222 0       0

Now, when you reboot Ubuntu, your NTFS windows partition will be available. Let me know if you got it

I hope this help.
Hoffmann

---

### Post by Hoffmann on 2006-04-28
[QUOTE=asjdfwejqrfjcvm msz34rq33]In the terminal type:
```
gconf-editor
```Then, in the left hand menu, go: **apps**, **nautilus**, **desktop**, and uncheck **volumes_visible**. That should fix it.[/QUOTE]

I have done that before. The problem is that not only the Windows icon was hidden, but also the CD-ROM or my external HD icons were hidden (after inserting a CD disk, or connecting to the external HD). Is it possible to hind just the windows partition icon?

---

