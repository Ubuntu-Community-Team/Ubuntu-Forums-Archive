---
title: "Getting Nvidia X Server settings to &quot;Stick&quot;"
date: 2010-05-10
forum: General Help
---

### Post by MechWarrior001 on 2010-05-10
Not sure if this is the right forum for Linux Mint but I heard it is based on Ubuntu so I figured it might be ok. Let me know if I'm wrong.

I'm having trouble getting the X server settings to stay when using the Nvidia X configuration tool on Linux Mint 9.10. Everytime I try to save to xorg.conf it gives me "Failed to parse existing X config file '/etc/X11/xorg.conf'!" even when using the sudo command. Any ideas?

---

### Post by scouser73 on 2010-05-10
Paste these commands into Terminal to create a new Xorg.conf, that should now have created a new xconfig file.

The first step creates a backup of your currently working xorg.conf file.
**> sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.bak**

Step 2 runs the NVIDIA utility to generate a new xorg.conf file that the utility can actually read.
**> sudo nvidia-xconfig**

Step 3 runs the graphical NVIDIA setup tool as root, so you can actually save your changes.
**> sudo nvidia-settings**

[COLOR="Red"]******[/COLOR] **_If it does not work then after step 1, please do the following_ [COLOR="Red"][B]****[/COLOR][/B] > **sudo rm /etc/X11/xorg.conf** to delete your current xorg.conf file. Then run > **sudo nvidia-xconfig** and finally > **sudo nvidia-settings**

---

