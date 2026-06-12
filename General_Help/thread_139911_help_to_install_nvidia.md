---
title: "help to install nvidia"
date: 2006-03-05
forum: General Help
---

### Post by drop_d33 on 2006-03-05
i tried this last night, following the steps in [https://wiki.ubuntu.com/BinaryDriverHowto/Nvidia](https://wiki.ubuntu.com/BinaryDriverHowto/Nvidia) in which i failed, or something went wrong. after the last step, when i pressed ctrl+al+backspace, the screen just went black and it never returned. i had to call my friend for help, who told me to type something that would retrieve my backup settings thru cp /backups//xorg...(cant remember the rest). now when i try to attempt the procedure again, when i type sudo nvidia-glx-config enable in the terminal, i get this: Error: your X configuration has been altered.
This script cannot proceed automatically. If you believe that this
not correct, you can update the md5sum entry executing the following
command:
md5sum /etc/X11/xorg.conf | sudo tee /var/lib/xfree86/xorg.conf.md5sum
otherwise edit manually /etc/X11/xorg.conf to change the Driver section
from nv to nvidia.
 i dont know what to make out of this. im scared of getting that black screen again. i dont want to lose ubuntu... please help. im just trying to make unreal tournament work. :cry:

---

### Post by drop_d33 on 2006-03-05
somebody help!

---

### Post by RAOF on 2006-03-05
Try running (from the console) **sudo dpkg-reconfigure -phigh xserver-xorg**.  It'll ask a couple of questions - just accept the defaults (incidentally, this is how you can fix your X server if you get the black screen again).  This should update the checksum so that nvidia-glx-config enable works.

Alternatively, just select the "nvidia" driver from the first list that dpkg-reconfigure gives you.  If that doesn't work, it would be usefull to have the X server log.  You can get just the errors by running **cat /var/log/Xorg.0.log | grep "(EE)"** at a terminal.

---

### Post by drop_d33 on 2006-03-05
hey thanks.. when i typed 
"sudo dpkg-reconfigure -phigh xserver-xorg" 
in the terminal, i get this:
xserver-xorg postinst warning: overwriting possibly-customised configuration
   file; backup in /etc/X11/xorg.conf.200603052050
really, im afraid to do anything.. im traumatized from the black screen.. i wouldnt want anything worse to happen

---

### Post by akiro.yamamoto on 2006-03-05
For some strange reason, sometimes the GDM will not restart. So if you are at the 
black screen, READ any messages / errors on the display.
If you see something like
login:
well type in your user name then press [ENTER]
then type in your password (Nothing will show, no stars ) press [ENTER]
and finally type
startx (this will start the gnome display.)
If you see something like
user@mycomputer:~$
well just type startx.

---

### Post by drop_d33 on 2006-03-05
when i got the black screen, i could literally do nothing. so i went into recovery mode, in which my friend advised me to type 
cp -v /var/backups//xorg/xorg.comf(cant remember the rest) -> /etc/x11/xorg
now i tried to retry the steps to install the nvidia thingy but after i type the
sudo nvidia-glx-config enable
i get this: 
Error: your X configuration has been altered.
This script cannot proceed automatically. If you believe that this
not correct, you can update the md5sum entry executing the following
command:
md5sum /etc/X11/xorg.conf | sudo tee /var/lib/xfree86/xorg.conf.md5sum
otherwise edit manually /etc/X11/xorg.conf to change the Driver section
from nv to nvidia.
then i tried:
sudo dpkg-reconfigure -phigh xserver-xorg
the output was:
xserver-xorg postinst warning: overwriting possibly-customised configuration
   file; backup in /etc/X11/xorg.conf.200603052117
i dont understand any of these.. scary really for a newbie like me

---

### Post by az on 2006-03-05
[QUOTE=drop_d33]
xserver-xorg postinst warning: overwriting possibly-customised configuration
   file; backup in /etc/X11/xorg.conf.200603052050
really, im afraid to do anything.. [/QUOTE]


Don't worry.  It is telling you that it will change the current configuration - which may probably be the problem.   You want to overwrite this file.

Close your eyes, trust apt, answer "yes" and use the force....

---

### Post by drop_d33 on 2006-03-05
so what should i do? everytime i type that command, it always gives me the same warning. whats the next step? i tried to 
sudo nvidia-glx-config enable
but got this
Error: your X configuration has been altered.
This script cannot proceed automatically. If you believe that this
not correct, you can update the md5sum entry executing the following
command:
md5sum /etc/X11/xorg.conf | sudo tee /var/lib/xfree86/xorg.conf.md5sum
otherwise edit manually /etc/X11/xorg.conf to change the Driver section
from nv to nvidia.
what does this command stated above do?:
md5sum /etc/X11/xorg.conf | sudo tee /var/lib/xfree86/xorg.conf.md5sum
 really have no idea on what to make out on all of these. im stuck. dont know what to do

---

