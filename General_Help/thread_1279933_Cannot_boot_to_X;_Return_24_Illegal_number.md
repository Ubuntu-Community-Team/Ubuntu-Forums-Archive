---
title: "Cannot boot to X; Return 24: Illegal number"
date: 2009-10-01
forum: General Help
---

### Post by apocryphalbeing on 2009-10-01
I installed splashy to replace usplash last night and then went back to usplash, as a program to control the loading screen on my fujitsu siemens laptop. (I installed splashy with some --force-overwrite command which i found because it wasnt installing properly, which i cant find at the moment) Now X won't start giving an error message :

" Could not start the X server (your graphical environment) due to some internal error. Please contact your system administrator or check your syslog to diagnose. In the meantime this display will be disable. Please restart GDM when the problem is corrected. "

Then drops me into the terminal. Recovery mode does the same thing eventually. The try and fix graphics settings (xfix) option doesn't work. 

The file system is also mounted as read only. As I understand this is because of the fstab option 'error=ro' ( or something similar). This I can get around temporarily by remounting as rw. Also most of the things it tries to run on boot, as well as some from the terminal don't work, merely giving: " Return 24: Illegal number: for almost all processes.

I fscked the partition from a live cd, which didn't do anything. I also tried 'sudo dpkg-reconfigure -phigh xserver-xorg' which didn't help either. 

I can't run startx or ./etc/init.d/gdm start

Also on logging from the command line  in I get several "-bash: /dev/null: Permission denied" errors ( which might be because it's mounted as read only.

Anybody has any idea how I can fix this?

---

