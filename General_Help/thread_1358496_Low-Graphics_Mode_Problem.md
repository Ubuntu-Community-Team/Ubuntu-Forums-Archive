---
title: "Low-Graphics Mode Problem"
date: 2009-12-18
forum: General Help
---

### Post by morisila.ardiel on 2009-12-18
I found a thread for dual monitoring here in the forums (and of course now I can't even find the thread) and while I was editing in the terminal, following the instructions of the thread, my screen blanked and restarted in "low graphics mode" I have been trying to fix this, getting multiple errors. I have an hp pavillion dv6000 laptop and am running 9.1.

When I hope my display to change the resolution, I get this:

It appears that your graphics driver does not support the necessary extensions to use this tool.  Do you want to use your graphics driver vendor's tool instead?

When I say yes, the nvidia X Server comes up, with a popup that says this:

You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server

So I open the terminal and do this

morisila@Deathtrap-2:~$ sudo nvidia-xconfig
[sudo] password for morisila: 

Using X configuration file: "/etc/X11/xorg.conf".
Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'

But when I restart the x-server, it all starts over again and still uses the low-graphics mode.

---

### Post by mikewhatever on 2009-12-18
You can reset xserver settings by booting in recovery mode and selecting xfix. Hope that works.

---

### Post by morisila.ardiel on 2009-12-24
Unfortunately that did not solve the problem, but I did reinstall 9.1 and the problem is solved.

---

### Post by s263030 on 2009-12-24
hi

go to [http://www.nvidia.com/Download/index.aspx?lang=en-us](http://www.nvidia.com/Download/index.aspx?lang=en-us)
 
and download your driver 

save it on the desktop

use  crtl+alt +f1  it will show tty1 (to go back to graphical mode use crtl+alt+f7)

login , and use these commands 

> sudo su

```
 /etc/init.d/gdm stop
```

```
cd ~/Desktop
``` 

> ./THE NAME OF THE FILE U DOWNLOADED 

wait until it finishes and reboot

> reboot

sorry for my bad English :)

---

