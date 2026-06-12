---
title: "Can't get ATI drivers working..."
date: 2006-03-01
forum: General Help
---

### Post by event on 2006-03-01
I can't seem to get this working. I have a 9000 Mobility. I followed this howto: [http://ubuntuforums.org/showthread.php?t=24557](http://ubuntuforums.org/showthread.php?t=24557)

I followed the instructions for installation of the drivers, but X always fails and I have to restore my old xorg.conf file.

I followed the instructions for reinstallation of the drivers, but when I try "sudo modprobe fglrx" i get the error message: ```
FATAL: Error inserting fglrx (/lib/modules/2.6.12-10-386/volatile/fglrx.ko): No such device
```
What is the deal with that? If I go through and edit the xorg.conf file and restart the X environment, it crashes and I'm stuck with no GUI.

---

