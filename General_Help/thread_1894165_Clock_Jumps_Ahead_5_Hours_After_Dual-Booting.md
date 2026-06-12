---
title: "Clock Jumps Ahead 5 Hours After Dual-Booting"
date: 2011-12-11
forum: General Help
---

### Post by Wiking on 2011-12-11
I have a dual-boot setup with Windows 7 and linux distro, for some reason whenever I boot into Windows 7 after being in Linux my clock is always 5+ hours ahead. I end up having to synchronize it with the time.windows.com server.

This only happens if I go from Linux to Windows. If I use Windows and shut off and restart multiple times the time stays correct, this only happens after I log off from Linux and restart into Windows 7

I asked around in a Windows forum and got this reply,

> It seems obvious that Linux is resetting your BIOS's clock and when you syncronize time in Windows, it is resetting the BIOS time. I can't remember clearly the details, but during installation of Linux, it gave the option of what time it was to use. Again, I'm not sure of the remedy, but somewhere in Linux, there is a way to reset this characteristic.

How can I reset the time in BIOS through Kubuntu?

---

### Post by Wiking on 2011-12-12
I found the solution to the problem using google.

Make a backup copy of /etc/default/rcS and then change UTC=yes to UTC=no.

---

### Post by Mark Phelps on 2011-12-12
To fix this, edit /etc/default/rcS 

Change the UTC line to say UTC=no

Reboot.

Now, both Linux and Windows will use the same (local) time.

---

