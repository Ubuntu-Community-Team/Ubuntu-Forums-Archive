---
title: "force gpu 3d speed"
date: 2009-09-23
forum: General Help
---

### Post by hwttdz on 2009-09-23
So I'm playing around with folding at home, and I've got gpu folding working through wine.  And it actually works quite well, but the gpu always reverts to 2d speeds.  Is there some way I can force it to run at 3d speeds?  Card is Nvidia GeForce 9800 GTX+.

Actually, I've just found two possibilities detailed here:
[http://www.ubuntusolutions.org/2009/02/screen-flickering-with-nvidia-on-ubuntu.html](http://www.ubuntusolutions.org/2009/02/screen-flickering-with-nvidia-on-ubuntu.html)
I'm going to hold off until I have physical access to the machine, but I'll give it a go soon.

Update: I had luck with the module options method.  Running 9.04.

---

### Post by hwttdz on 2009-12-11
The first solution, namely adding

```
options nvidia NVreg_RegistryDwords='PerfLevelSrc=0x2222'
options nvidia NVreg_Mobile=1
```

to /etc/modprobe.d/options.conf worked for me.

---

