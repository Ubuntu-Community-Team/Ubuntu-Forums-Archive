---
title: "increasing icon size on Gnome panel"
date: 2011-11-25
forum: General Help
---

### Post by rmcellig on 2011-11-25
My Mom is running Ubuntu 11.04 on her old Dell 4500S desktop. I created a top panel for her so that she has easy one click access to the places she visits most. She wanted to know if it is possible to increase the size of the icons on the panel because she has trouble seeing. Any ideas?

---

### Post by Old_Grey_Wolf on 2011-11-25
Right click on the panel, select Properties, in the Size menu double the number of pixels.

---

### Post by rmcellig on 2011-11-25
That seems to increase the size of the  panel but the icons  don't increase in size.

---

### Post by Old_Grey_Wolf on 2011-11-25
What DE are you using; such as, Gnome 2, Gnome 3, Unity? What works on Gnome 2 may not work if you are using Unity.

---

### Post by Bobhuber on 2011-11-25
> **rmcellig said:**
> My Mom is running Ubuntu 11.04 on her old Dell 4500S desktop. I created a top panel for her so that she has easy one click access to the places she visits most. She wanted to know if it is possible to increase the size of the icons on the panel because she has trouble seeing. Any ideas?
My Mom has the same problem. My solution was to use cairo-dock and the compiz screen magnifier. Make sure you install all of the compiz addons. There are two magnifiers in compiz. One full screen and one that you can specify size.I'm using gnome3 right now so I'm quoting all this from memory (which fails an old man at times). Cairo dock allows you to create a launcher that uses a keyboard shortcut.I used the keyboard sequence (I forgot exactly what it is) that launches the magnifier in compiz to  creat a launcher in cairo-dock that she can click on and drag the magnifier anywhere on the screen she needs it.You can make the launcher in CD as large as you need it and autohide it when not in use to save screen space if needed.

---

### Post by rmcellig on 2011-11-25
Thanks Bobhuber! My Mom will  be using a HP laptop that we gave her a few years ago for her birthday. Right now  she is using an old Dell desktop with a 15" monitor. She asked me if it's possible to transfer  her current setup to the laptop. I remember something called Remastersys that I think would be able to do this but it has been replaced by something else.

---

### Post by Bobhuber on 2011-11-25
> **rmcellig said:**
> Thanks Bobhuber! My Mom will  be using a HP laptop that we gave her a few years ago for her birthday. Right now  she is using an old Dell desktop with a 15" monitor. She asked me if it's possible to transfer  her current setup to the laptop. I remember something called Remastersys that I think would be able to do this but it has been replaced by something else.
Fsarchiver will do what you want, After using that you will need to install grub for your distro on the laptop with a live CD. Just make sure the laptop drive is partitioned and formatted for linux (not windows) before installing the backup. System-Rescue-CD has this utility along with everything you will need to format and patiton the drive. The ISO can be found here.
 [http://www.sysresccd.org/Download?site=gooplusplus.com](http://www.sysresccd.org/Download?site=gooplusplus.com)

---

### Post by tersogar on 2011-11-25
I help my mother in law with the universal access. There you can make selection that best work for you.

---

### Post by rmcellig on 2011-11-25
> **Bobhuber said:**
> Fsarchiver will do what you want, After using that you will need to install grub for your distro on the laptop with a live CD. 
 [http://www.sysresccd.org/Download?site=gooplusplus.com](http://www.sysresccd.org/Download?site=gooplusplus.com)

So the System Rescue CD should have a boot loader GRUB utility on it? If so, that's great. I am hoping that FS Archiver is a GUI app. Will check it out.

Randy

---

