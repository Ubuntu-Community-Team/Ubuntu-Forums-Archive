---
title: "Xorg settings"
date: 2010-02-03
forum: General Help
---

### Post by JKoder on 2010-02-03
Dear ubuntu user. I have a small question for anyone who can help.
I noticed Ubuntu 9.10 does not have an XORG file.Everything is working just fine so far BUT what is i need some spoecial settings for X ? where and how can i define them ?

For example, to have a functional S-Video output i need 2 options one of them if ForceTVout i think.
Now , since i dont have an xorg.conf file, where can i specify this option ? 
Or do i need an xorg.conf file ? -- if so, can ubuntu generate one for me based on my current video settings ?

Thank you !

---

### Post by scouser73 on 2010-02-03
Paste these commands into Terminal to create a new Xorg.conf, that should now have created a new xconfig file.

The first step creates a backup of your currently working xorg.conf file.
**> sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.bak**

Step 2 runs the NVIDIA utility to generate a new xorg.conf file that the utility can actually read.
**> sudo nvidia-xconfig**

Step 3 runs the graphical NVIDIA setup tool as root, so you can actually save your changes.
**> sudo nvidia-settings**

If this does not work then after step 1, do **sudo rm /etc/X11/xorg.conf** to delete your current xorg.conf file. Then run **sudo nvidia-xconfig** and **sudo nvidia-settings**.

---

### Post by JKoder on 2010-02-03
> **scouser73 said:**
> Paste these commands into Terminal to create a new Xorg.conf, that should now have created a new xconfig file.

The first step creates a backup of your currently working xorg.conf file.
****

Step 2 runs the NVIDIA utility to generate a new xorg.conf file that the utility can actually read.
****

Step 3 runs the graphical NVIDIA setup tool as root, so you can actually save your changes.
****

If this does not work then after step 1, do **sudo rm /etc/X11/xorg.conf** to delete your current xorg.conf file. Then run **sudo nvidia-xconfig** and **sudo nvidia-settings**.
Ok, but :
1. I dont have an xorg.conf file, so i dont have anything to backup.
I need a new xorg file based on what ubuntu knows about the graphic system ( that is runnig without an xorg)
2. I dont have nvidia, i have ATI and i'm using the opensource drivers.
So any other suggestions ?

---

### Post by scouser73 on 2010-02-03
This creates a new xorg file, as for ATI I'm sorry I can't help you with that.

> **sudo nvidia-xconfig** 

---

