---
title: "How to Configure to run in Failsave Graphics?"
date: 2011-03-07
forum: General Help
---

### Post by Quarkrad on 2011-03-07
Running 10.10 and graphics card has just died. I have to start in recovery mode from grub screen and manually request failsafe graphics. For some reason Ubuntu will not Reconfigure my graphics set up, so everytime I switch on I have to go through the screens to run in failsafe mode.  Can I do something so that Ubuntu will just boot in this mode?  I will replace the card but it may take some time.  My monior is currently plugged into the motherbord which is a ASROCK G31M - R2.0 which has Intel® Graphics Media Accelerator 3100 graphics.

---

### Post by kiyop on 2011-03-07
If you have not change /etc/X11/xorg.conf and have not install any graphics drivers,

"Application" -> "Accessory" -> "Terminal"

$ gksu gedit /etc/default/grub

Change the line:
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
to
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash xforcevesa"

Save and quit text editor.

Execute
$ sudo update-grub
in order to activate the change.

____________________

If you have changed /etc/X11/xorg.conf and/or have installed some graphics drivers,
you may have to execute
$ sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.old-backup
and/or have to uninstall driver by synaptic or so.

---

### Post by Quarkrad on 2011-03-07
Thank you - I forgot to mention that i'm a newbie!  I am OK with what you are asking me to do but I did not mention that I use Burg as my graphical grub.  I believe (although I could be wrong) that Burg 'takes over' from grub - are the instructions you gave me in the last post still OK.  Apologies for this - I appreciate the help.

---

### Post by kiyop on 2011-03-07
I am not familiar with BuRg.
[https://help.ubuntu.com/community/Burg#See%20Also](https://help.ubuntu.com/community/Burg#See%20Also)

Editing /etc/default/burg and
$ sudo update-burg
may alter the settings, though I am not sure.

---

### Post by Quarkrad on 2011-03-08
The burg commands worked - many thanks.

---

