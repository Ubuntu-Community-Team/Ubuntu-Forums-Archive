---
title: "Computer freezes during installation"
date: 2006-03-23
forum: General Help
---

### Post by surferben182 on 2006-03-23
I have tried to install 5.10 and it always freezes.  This happened last time and it turned out i had bad memory, but i did a memtest and it said i was fine.  I also did a CPU burn which also came up clean.

It froze at 71% of Installing Packages: Configuring ACPI-support.

i tried disabling the ACPI during the installation (im not even sure what ACPI is) but that also failed.

any help?

---

### Post by Clark_Bent on 2006-03-23
I am having the exact same problem at the exact same stage of the install. I have done the following so far:

1. Downloaded two new ISOs and burned them (Drapper Flight and Breezy)
2. Attempted the install on different hard drives.
3. Ran memtest
4. Did a server only install
5. Disabled ACPI

Now when I did the server only install, I was excited as I thought I had this whipped. I got a nice little shell. I thought ok...I'll just apt my desktop and it died at the exact same point.

I have ran Debian Sid AMD64 on this same box with no troubles at all. I am a desperate fool at the end of my rope. I have no ideas left. Strange that we are locking up at the same stage. Makes me feel a little better...as in it's not looking like bad hardware.

---

### Post by Clark_Bent on 2006-03-24
BUMP

If anybody can help, I would be most grateful.

---

### Post by rfruth on 2006-03-24
It sounds like a hardware or compatibility problem, does a live CD do okay, is there somekind of BIOS burn in / test ?

---

### Post by Clark_Bent on 2006-03-24
Haven't tried a live CD, but as I mentioned, I was running Debian AMD64 Sid with no trouble on this same box. I read in one of the other threads that 5.10 has a bug in the installer. Going to give 5.04 a go now. I can always upgrade through apt. If it works, I'll post back and hopefully the other poster will get lucky too.

---

### Post by ed_agamemnon on 2006-03-24
If things get really miserable you could try an internet install...

---

### Post by Mustard on 2006-03-24
You could also try fiddling around with the ACPI settings in BIOS.

---

### Post by Clark_Bent on 2006-03-25
Appreciate the responses. My first go around with hoary failed...however it made it past the ACPI point where I was having trouble prior. Now it is freezing on installing xlib. So I reinstalled, only as server this time and did a apt get update and am now apting the desktop, however I suspect it will freeze again at xlib. I have a dreaded ATI card, so I am sure I will have trouble there. So surferben, if your still trying and you don't have a ATI card, hoary just might be your way out. For me there is a excellent chance I'll be going back to Debian. At least it works with common hardware. Pretty amazing that Ubuntu is so far off in this regard with the amount of praise it has got.

---

