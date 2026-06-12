---
title: "USB Drives Opening with Banshee instead of Nautilus"
date: 2011-10-17
forum: General Help
---

### Post by J.L.C. on 2011-10-17
I upgraded to 11.10 from an 11.04 install and the system seems to get confused between Nautilus and Banshee.

Whenever I insert a USB drive (either stick or external hard drive), Banshee launches - even though there are no audio or video files on the drive.

I selected "never prompt or start programs on media insertion" in System Settings and now Banshee isn't starting automatically.

However, if I click the mounted USB file system in the Launcher...Banshee starts up rather than Nautilus.

Is this something I can change with a setting somewhere? Is it a bug?

---

### Post by mc4man on 2011-10-17
Alot of this lately
```
gedit ~/.local/share/applications/mimeapps.list
```

Look for the line in the [Default Applications] section 
inode/directory=
delete it entirely 
Or post the contents of the file

---

### Post by J.L.C. on 2011-10-17
That fixed it :)

Thanks!

---

### Post by mc4man on 2011-10-17
if you get a chance - what did that line have on the 
inode/directory=
Was it nautilus-folder-handler.desktop or banshee.desktop or therabouts

---

### Post by J.L.C. on 2011-10-17
I had:

inode/directory=nautilus-folder-handler.desktop

Kind of counter-intuitive since nautilus is what I wanted and what was listed, but Banshee was always launching.

---

