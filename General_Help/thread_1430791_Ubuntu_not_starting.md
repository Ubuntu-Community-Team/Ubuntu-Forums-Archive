---
title: "Ubuntu not starting"
date: 2010-03-15
forum: General Help
---

### Post by RonB123123 on 2010-03-15
Once I select Ubuntu 9.10 from Grub, it shows the logo, the logo disappears, a jet black screen shows with 2 horizontal white dashes appear at the top.

I recently uninstalled Firefox 3.6 pre using synaptic to go with the stable Firefox 3.6 installed with the PPA repository that was given in the Ubuntu wiki. It installed and ran fine but when I rebooted, ubuntu wouldn't start.

I went into recovery mode a few times, tried to fix any broken packages and when it said it was fixed, I tried rebooting and the same error occurred. I also tried to use dpkg-reconfigure for the xserver-xorg and then ran startx but x didn't load properly. Some more debugging and a few driver errors came up involving intel so I installed a package which fixed that. 

Ran the dpkg-reconfigure again and ran startx. This time x loaded but it was a jet black screen and I had to hold ctrl + alt and hit a few F keys to get back to the prompt. 

I understand this could be a xulrunner error so I tried reinstalling xulrunner-1.9.1. I also rolled back my repositories to get the Firefox 3.5 branch and I installed the original Firefox 3.5, ran firefox --version to make sure and I finally have that back installed.

I tried rebooting and running the OS normally, but again it failed at the same point. What exactly should I do next? Yes, I could reinstall but it's such a small problem with maybe 1 or 2 broken packages, is there anyway I can save my current ubuntu system (as I have made countless configuration changes months ago and I do not want to do it again)? 

Is it possible to fix it? Thank you,

Ron

---

### Post by RonB123123 on 2010-03-23
My ubuntu box wasn't working but my windows vista was working so I used this software to mount my ext3 partition onto windows in order to copy my files over.

Ext2/Ext3/Ext4 Installable File System for Windows
[http://www.fs-driver.org/](http://www.fs-driver.org/)

Once I did that, I used EASEUS partition manager to delete the Linux partition and Vista crashed and gave me a blue screen. I rebooted and grub was messed up and didn't reload the MBR so I was stuck without an OS.

I booted with the Linux live CD and use the partitioning software through the Install Linux icon (GParted) and was able to successfully install over my old linux partition as well as my old swap partition. Now I have a clean install of Ubuntu 9.10 working which fixed grub so I can load vista as an alternative.

I wish I was actually able to fix the problem but from now on I'm not going to install any unstable software by mistake and then uninstall it and reinstall stable software because if I reboot then suddenly I'll have a **** load of problems that would be easier to fix by reinstalling.

I still have the same issue with the ALSA sound driver where I won't have working sound until I run the command:
sudo /sbin/alsa force-reload

I also have the same issue with my wireless controller where it will be connected to a router but it will drop the connection, try to reconnect, then fail, and it then gives up completely forcing me to reboot the system. There must be an easier way to reload the wireless controller like the alsa driver to get it to start working again without having to waste time rebooting.

Hope this helps anyone with a similar issue.

---

