---
title: "Hoary and nvidia drivers: system slowness"
date: 2005-02-13
forum: General Help
---

### Post by Psyk[o] on 2005-02-13
I'm running Ubuntu Hoary and I want to use the nvidia driver for my FX5200.
I've installed the latest kernel avaible (2.6.10-3), the linux-restricted-modules-2.6.10-3 package and nvidia-glx package.
I've configured the /etc/X11/xorg.conf commented the GLCore and dri lines, and I've changed in device section from "nv" to "nvidia", then I've do "modprobe nvidia". 
The X server start without any problem, I see the nvidia logo but the system is damn slow, glxgears runs at 1-2fps, the application take 10-20 seconds to start and sometimes the mouse pointer dissapear...
I cant understand where is the problem :( anyone can help me?  ](*,)

---

### Post by scoon on 2005-02-14
[QUOTE='Psyk[o]']I'm running Ubuntu Hoary and I want to use the nvidia driver for my FX5200.
I've installed the latest kernel avaible (2.6.10-3), the linux-restricted-modules-2.6.10-3 package and nvidia-glx package.
I've configured the /etc/X11/xorg.conf commented the GLCore and dri lines, and I've changed in device section from "nv" to "nvidia", then I've do "modprobe nvidia". 
The X server start without any problem, I see the nvidia logo but the system is damn slow, glxgears runs at 1-2fps, the application take 10-20 seconds to start and sometimes the mouse pointer dissapear...
I cant understand where is the problem :( anyone can help me?  ](*,)[/QUOTE]


Hey there, 

Got to nvidia.com and read the README.txt.  That will give you ALL of the help for speeding up your driver that you could possibly need. 


scoon

---

