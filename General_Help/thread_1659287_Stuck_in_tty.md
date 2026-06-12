---
title: "Stuck in tty"
date: 2011-01-03
forum: General Help
---

### Post by mmsmc on 2011-01-03
im am stuck i tty because there is something wrong with my nvidia driver(iv already come to that conclusion) and i was wondering if there was a way to deactivate the driver from the terminal?

---

### Post by JC Cheloven on 2011-01-03
Quick'n'dirty solution would be to uninstall everything nvidia related, and reboot. So at a terminal you can type [COLOR="Blue"]sudo apt-get remove nvidia[/COLOR] and then press tab twice. You'll be presented with a list of every installed packages starting by "nvidia". Then you can add them to the remove line you were writting. I can't give a smarter advice at this moment, as I think xorg.conf is not longer used in ubuntu.

Just in case: You can (try to) fire up the desktop environment by [COLOR="Blue"]sudo service gdm start[/COLOR] (stop to close it). And ctrl-alt-F1 (to F6) brings you to six different tty's. ctrl-alt-f7 usually brings you to the graphical desktop, if running.

Hope this helps.

---

### Post by mmsmc on 2011-01-03
it says that the gdm is already running???
and uninstallinng did not work:mad:
this sucks

---

### Post by wojox on 2011-01-03
See if this still works:

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by mmsmc on 2011-01-03
nothings up happens, it just brings up another command line
ive been doing a little playing around heres what happened


when nvidia-xconfig is entered it gives me: validation error data incomplete in file etc x11 xorg.conf
i did some searching and found this line: sudo nvidia-xconfig
now nvidia-xconfig gives me this:
using X configuaration file: "/etc/X11/xorg.conf".

ERROR: unable to wright to directory '/etc/X11'.




hope this reveal anything wrong!


I also cant update or upgrade anything because i cannot connect to my wireless internet without loging on

---

### Post by wojox on 2011-01-03
If you uninstalled all the nvidia drivers then *sudo nvidia-xconfig* won't help. Run my above command again and reboot. It should load the default driver for Ubuntu.

---

### Post by mmsmc on 2011-01-03
no, its still loading up into tty

---

### Post by mmsmc on 2011-01-03
ok i did it(must have not been fully uninstalled) it passed the tty, and now it is just stuck at the ubuntu loading screen!

---

