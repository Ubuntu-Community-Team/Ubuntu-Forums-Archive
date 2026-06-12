---
title: "How to uninstall within XP"
date: 2009-07-30
forum: General Help
---

### Post by Shado1 on 2009-07-30
I installed Ubuntu inside a Windows XP machine, I did not create a new partition, just installed inside XP.  I need to remove Ubuntu, but don't know how.  When Ubuntu is deleted will this also fix the boot loader so my machine will start XP automatically?  I'm a complete noob with Ubunto.

---

### Post by lisati on 2009-07-30
If you used "wubi" to install Ubuntu the first port of call for uninstalling Ubuntu is on the Windows control panel entry "Add/remove programs" - same as for other stuff that you install "inside" Windows

---

### Post by philcamlin on 2009-07-30
you installed wubi so look here :)

[https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20uninstall%20Wubi?](https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20uninstall%20Wubi?)

:popcorn: look for uninstall ubuntu

---

### Post by stlsaint on 2009-07-30
good ol wubi...easy install easy uninstall!! add/remove...its just considered another program to windows!!

---

### Post by Shado1 on 2009-07-30
Ok I ran the uninstall from the control panel, but when I rebooted it still asks if I want to load Windows XP or Ubuntu.  How do I get that changed back?  I did verify that the folder was deleted from my C: drive.

---

### Post by DeMus on 2009-07-30
> **Shado1 said:**
> Ok I ran the uninstall from the control panel, but when I rebooted it still asks if I want to load Windows XP or Ubuntu.  How do I get that changed back?  I did verify that the folder was deleted from my C: drive.

In C:\ you find a file called boot.ini. It could be hidden since it is a system file.
Make hidden files visible through the configuration screen.
Double click boot.ini so it will open in a text editor. Delete the line which says Ubuntu so it will only have the line with XP left.
Reboot and see what happens.

---

### Post by Shado1 on 2009-07-30
Thanks, that did the trick.  I just wanted to try Ubuntu to see what it was like.  I building a new media server soon and will do a full install on my current machine.  Thanks for all the responses.

---

