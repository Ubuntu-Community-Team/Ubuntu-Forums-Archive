---
title: "installing xp with virtualbox on ubuntu 10.04"
date: 2010-11-05
forum: General Help
---

### Post by tyltong123 on 2010-11-05
Hello, total Ubuntu noob here, so I just installed virtualbox today and I tried installing windows xp with it. Here are the steps that I did
I did a quick partition and it goes through all the windows xp installation screens and on the restart after the install, Blue screen of death and it would restart again and prompt me to choose "start window normally" and other choices and no matter what i select the blue screen comes up and it would restart again. anyone know why it's doing this?

---

### Post by rcayea on 2010-11-05
This is a total guess but it sounds like a bad disc. Have you ever used the disc before?

---

### Post by tyltong123 on 2010-11-05
> **rcayea said:**
> This is a total guess but it sounds like a bad disc. Have you ever used the disc before?

That's what i was thinking also and it's not a disk :) iso file

---

### Post by 3Miro on 2010-11-05
Is this the one from the Software Center (OSE) or from the Virtual Box web-page (PUEL). Check with the VB settings to see if you have 2D or 3D acceleration enabled (right click on the windows XP virtual machine and bring up settings/properties). This causes trouble sometimes.

You can try to enable/disable some options on it to see if it helps. Virtual Box installs can go wrong on many different levels and they are hard to figure out. You may have bad XP disk, you may have a non-standard copy of XP, there may be something specific about your CPU that makes Virtual Box less stable ... Try the settings and try to disable USB/Networks, increase/decrease RAM and video memory, some of that may help.

---

### Post by tyltong123 on 2010-11-05
> **3Miro said:**
> Is this the one from the Software Center (OSE) or from the Virtual Box web-page (PUEL). Check with the VB settings to see if you have 2D or 3D acceleration enabled (right click on the windows XP virtual machine and bring up settings/properties). This causes trouble sometimes.

You can try to enable/disable some options on it to see if it helps. Virtual Box installs can go wrong on many different levels and they are hard to figure out. You may have bad XP disk, you may have a non-standard copy of XP, there may be something specific about your CPU that makes Virtual Box less stable ... Try the settings and try to disable USB/Networks, increase/decrease RAM and video memory, some of that may help.

The 2D or 3D is disabled, I didn't mess with the setting when creating the xp, i just used all the reconmended settings. I'll mess with it and I'll test out the xp iso file i have on my desktop to see if it works. I've used virtualbox on my windows 7 desktop just trying it out on ubuntu, thanks for the responds.

---

### Post by 3Miro on 2010-11-05
You can try the XP cd under Virtual Box under Windows 7 so that you can make sure that the CD is OK.

---

