---
title: "Ubuntu Dual-Boot menu uninstall?"
date: 2009-10-13
forum: General Help
---

### Post by origamitech on 2009-10-13
I downloaded and burned the Ubuntu 9.04 CD.
I then tried to boot from it by having it in the CD drive at boot-up.
Windows XP ignored it and booted as usual.
I installed the boot-helper from the CD (wubi.exe).
This worked, and was given a boot-menu with 2 options:
> Windows XP Professional
> Ubuntu

So i selected Ubuntu, did NOT install, i only wanted to try it out.

Now, however, whenever i boot my computer (with or without the ubuntu disc)
i always get the dual-boot menu, even though Ubuntu is not installed or available to the device in any way.

Any ideas how to fix?

---

### Post by antonkedrov on 2009-10-13
hello.
i'm advise you to check following commands: fixboot and fixmbr.
you can find information about these commands in Google Search.

---

### Post by dwith on 2009-11-18
Neither *fixmbr* or *fixboot* solves the problem.

Is this a registry key issue? If so, how is this problem alleviated? Sometimes *Ubuntu* (Wubi installed) appears in the *Add-Remove Programs *section even though it has been removed. Manually removing *Wubildr* and the Ubuntu file under C: . After these files have been removed and Ubuntu installation removed from the *Add-Remove Programs * section, "Ubuntu" still appears in the boot menu options. While this may not be totally destructive, it takes over 20 seconds without hitting the return key to get the default operating system (Windows XP) to start. I used Wubi on a laptop that I will be giving to someone who is not technically minded. I re-wrote (fixmbr, fixboot) the master boot record and this did not take care of the problem. It is almost like the laptop now has a Ubuntu scar that won't go away--not that I don't like Ubuntu, but the person I am giving the laptop to doesn't appreciate Linux.

---

### Post by GeorgeOfTheBush on 2009-12-24
any suggestions on removing "ubuntu" from the windows boot options??

---

### Post by maxrpowell on 2009-12-24
not sure if this will work but you can give it a try; start your computer in windows, open wubi, it will tell you a previous installation was detected and needs uninstalled before you can continue, uninstall and then cancel when it comes to the screen that asks for you to select all your options for your installation. hope it works for you.

---

### Post by GeorgeOfTheBush on 2009-12-24
launching wubi did not help.

---

### Post by oldfred on 2009-12-24
Look in boot.ini it should have the wubi line you are seeing. Be careful editing it, but that should fix it. If not sure make a backup first.

---

### Post by QLee on 2009-12-24
[QUOTE=origamitech]...
I installed the boot-helper from the CD (wubi.exe).
...
Any ideas how to fix?[/QUOTE]

If you installed an .exe, did the Windows installer do it for you, and if so, is there someplace in the windows control panel where you can uninstall? That used to be the way it worked, but I don't use Windows now, not sure about newer versions.

---

