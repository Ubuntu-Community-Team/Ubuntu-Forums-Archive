---
title: "Dual Monitor default?"
date: 2010-01-10
forum: General Help
---

### Post by InfamousLegato on 2010-01-10
Whenever I reboot my computer, my second monitor isn't activated and I have to manually set it up again.

---

### Post by bpalone on 2010-01-10
Check this thread, if you are using NVidia it should:

[http://ubuntuforums.org/showthread.php?t=1363997](http://ubuntuforums.org/showthread.php?t=1363997)

---

### Post by scouser73 on 2010-01-10
Please follow these instructions for setting up dual monitors with nVidia graphics cards only.

**1** - Paste this command into terminal: **gksudo nvidia-settings**

**2** - **X Server Display Configuration** will now start, now you can set up your monitors to your liking

**3** - Once you have done so click **Apply** then click **Save To X Configuration File**

You will now have dual monitors working.

---

### Post by InfamousLegato on 2010-01-10
I get the following error message 

First time I tried it I did the following

sudo mv -i /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
sudo tough /etc/X11/xorg.conf
gksudo gedit /etc/X11/xorg.conf

Section "Device"
Identifier "Configured Video Device"
Driver "nvidia"

sudo nvidia-settings 

PARSE ERROR: Parse error on line 3 of section Device in file /etc/X11/xorg.conf.
Unexpected EOF. Missing EndSection keyword?

Segmentation Fault

Second time I made a blank .conf file and saved it. 

Failed to parse existing X config file '/etc/X11/xorg.conf'!

Terminal says

VALIDATION ERROR: Data incomplete in file /etc/X11/xorg.conf
At least one Device section is required 

Segmentation fault
[B]
*EDIT*[/B]

Went back into terminal and did the following

sudo rm /etc/X11/xorg.conf
sudo rm /etc/X11/xorg.conf.backup
sudo nvidia-xconfig
sudo nvidia-settings

Was able to save my new xconfig file. Problem solved. Thank you for the help.

---

