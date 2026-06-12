---
title: "learning is tough - but the only way"
date: 2011-06-16
forum: General Help
---

### Post by Arun_W-mech on 2011-06-16
Hi everybody
I just installed ubuntu, to learn how it works.
The way I see it, I have a lot to learn.
I would like to ask if anyone have an answer why i can't see the content in my ISO files.
furthermore i have tried to install Fallout 3 (Windows version), using playonlinux.
when it is installed it says that fallout configutator encountered an error.
can anyone help me out on this

---

### Post by seawolf167 on 2011-06-16
Welcome to the forums!

In order to see the content of an iso file, you first have to mount it. [Here ]("https://help.ubuntu.com/community/MountIso")is the step by step walkthrough on mounting iso files in Ubuntu.

As for Fallout 3, I couldn't answer the question about PlayOnLinux, but I can point you to the [WineHQ article ]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=14322")on how to install it and what works and what doesn't work.

You will need Wine for this

```
sudo apt-get install wine
```Here is a good [starting point ]("http://ubuntuforums.org/showthread.php?t=801404")in general for learning about Ubuntu

---

### Post by Arun_W-mech on 2011-06-16
Hi Seawolf
Thanks for the reply
I have now installed Gisomount, but it looks like it rejects my iso's.
here's a shot of the message,
Thanks for the help 

Arun_W-mech

---

### Post by seawolf167 on 2011-06-16
I guess the question now is - how did you get or make the .iso file? Are you sure it is an .iso file? 

Can you mount it manually following the command line instructions from the link in my previous post?

---

### Post by Arun_W-mech on 2011-06-17
I either downloaded them or made them my self, i used ultraiso
and yes i can mount them, but when i open the mounted file all i see is an empty folder

---

### Post by LordNeo on 2011-06-17
That's because the iso is "double layer". You need to install the package for it. IIRC it's something like "iso9660" the format for those iso files.
Try installing something like "ImgBurn" that should install the needed dependency for you.

---

