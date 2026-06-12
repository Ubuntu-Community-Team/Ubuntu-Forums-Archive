---
title: "cannot save changes to X (resolution)"
date: 2006-05-20
forum: General Help
---

### Post by durableapostle on 2006-05-20
I am trying to change my screen resolution to a larger size.

Here's my problem:

I go through the process of backing up my "stuff" (/etc/X11/xorg.conf /etc/X11/xorg.conf.bak). I then reboot, and my screen stays the same. When I check the "new" /etc/X11/xorg.conf, it is exactly as it was before.

When rebooting, I am reversing the process above (/etc/X11/xorg.conf.bak /etc/X11/xorg.conf), then startx.

Obviously, I'm doing something wrong--probably something simple--but hey, I'm a complete n00b here, more than words can say....

Any suggestions?

---

### Post by crashtest on 2006-05-20
I'm not sure why your changes are not being saved, but I can save you a little time while you troubleshoot.  There is no need to reboot - simply kill the xserver with ctrl-alt-backspace.

---

### Post by bluevoodoo1 on 2006-05-20
This guide might be of some use...
[http://doc.gwos.org/index.php/ChangeResolution](http://doc.gwos.org/index.php/ChangeResolution)

you might want to write some of the commands down (especially the last two)... 
sudo dpkg-reconfigure xserver-xorg
and
sudo /etc/init.d/gdm stop
sudo /etc/init.d/gdm restart


(while using "sudo dpkg-reconfigure xserver-xorg" use the space bar to select something and the tab button to switch between items) You will have to use the space bar to select the correct resolution you want to use.

---

