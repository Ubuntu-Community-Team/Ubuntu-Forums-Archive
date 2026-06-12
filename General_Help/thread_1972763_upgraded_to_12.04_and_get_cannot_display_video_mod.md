---
title: "upgraded to 12.04 and get cannot display video mode"
date: 2012-05-03
forum: General Help
---

### Post by marcdonovan on 2012-05-03
so im hosed....

Tried the shift key on boot, no luck.

Help!!!

---

### Post by papibe on 2012-05-03
Hi marcdonovan.

Sorry to hear that.

Could you describe your problem a little bit more?
I believe you are not able to get into grub?
Are you booting into a complete black screen?
Have you tried going into text mode by pressing Ctrl+Alt+F1 ?

Regards.

---

### Post by marcdonovan on 2012-05-04
I turn on the PC, i immediately goes to a screen that says:
Cannot Display this Video Mode
Optimum resolution 1440x 900 60Hz

Ctrl/Alt/F1 does nothing

---

### Post by papibe on 2012-05-04
My guess is that your xorg.conf have something that is not compatible with your monitor.

I would try to remove it (rename it actually).

I see 2 options:
1. Boot into recovery mode to get into text mode. Keep shift pressed while booting to get into the grub menu. There choose to boot into recovery mode. Once you logged on, run this:
```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.old
```

2. Use the installation CD/USB as a Live CD and once you get to the desktop, mount the local HD and rename the file (try not to get confuse with the one on the live CD).

I hope one of those ideas work.
Regards.

---

### Post by marcdonovan on 2012-05-05
That did not work. I don't think xorg.conf is loaded until later in the process. I searched for a solution for grub and I found something @linuxquestios.org

update /etc/default/grub w these lines
GRUB_GFXMODE=640x480
GRUB_GFXPAYLOAD=640x480

then run 
sudo grub-update
which updates some other file
I also saw advice to use this:
GRUB_CMDLINE_LINUX="video=VGA-1:640x480"

My problem now is how to do this using a live cd. Since grub-update is trying to change the wrong config file. Is there a way to run a shell with my /dev/sda1 as the "root"?

I was considering doing this on another computer and then run a diff to see what changes in the grub config file.

---

### Post by pradeepsmk on 2012-05-27
same prob.  
i waited on that screen for 15 to 20 seconds (after first reboot)

then the desktop showed up.

grub boots up the default OS if no input received from keyboard. 
(any key hit will stop the count-down)

after logging in, edited the /etc/default/grub file (sudo gedit ...) , uncommented the GRUB_GFXMODE=640x480 by removing # prefix, saved it and ran a update-grub (sudo update-grub)

i could see grub  after reboot

---

