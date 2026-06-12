---
title: "restart without hard boot."
date: 2010-01-30
forum: General Help
---

### Post by soryu on 2010-01-30
are there any key's i could hit to restart karmic without doing a hard boot.

after my pc hibernates i wake it up but only get a black screen and forced to hardboot.

---

### Post by NightwishFan on 2010-01-30
Power management is problematic on some machines. If the machine is stuck, you can always try CTRL+ALT+DEL to force it to reboot, though that does not always work. On my machine, hibernation works but I have to hard reboot if I try to suspend.

---

### Post by mushwars on 2010-01-30
IF you cant see the screen but the computer is not frozen, what I do is ctl + alt + f2 into tty2 and then login as root, you may not be able to see it but you can still log in, then type halt or reboot and it will shutdown or reboot respectivly. good luck ;)

I have to do it all the time on my laptop because I compiled my kernel and didnt have laptop pannel support.

---

### Post by mionescu on 2010-01-30
You can try Ctrl-Alt-Backspace to restart only the X-server. I assume that your system is set-up to use this combination of keys to restart the X-server (see [http://www.ubuntu.com/getubuntu/releasenotes/910](http://www.ubuntu.com/getubuntu/releasenotes/910) down to "Ctrl-Alt-Backspace disabled by default in Xorg, configured via XKB" how to set it up). Alternatively, you can type Ctrl-Alt-F1 and then login in the terminal and type 
sudo restart gdm
(if you use ubuntu) or
sudo restart kdm
(if you use kubuntu)
If you use  version 9.04 or earlier the above commands will be
sudo /etc/init.d/gdm restart

---

