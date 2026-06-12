---
title: "Nvidia driver. No openGL after driver re-install"
date: 2009-07-14
forum: General Help
---

### Post by Sweetdaddydong on 2009-07-14
Ok so I tried to install the cuda video driver but things didn't quite work out.  I performed a kfix from the system recovery menu and that got my GUI(KDE desktop environment) up and running but when I went to re-install the old nvidia driver that is installed by the Hardware Drivers program a lost the GUI again. So I used apt-get remove to get rid of the old driver and re-installed again. I have the GUI running now but no desktop effects. I open up the nvidia settings program and select the OpenGL tab and it says that "Fail to query the GLX server vendor."

Anyone have any ideas how to get my desktop effects back or do I have to re-install?

thanks in advance

---

### Post by scrooge_74 on 2009-07-14
reboot again

---

### Post by Sweetdaddydong on 2009-07-14
> **scrooge_74 said:**
> reboot again

I've rebooted many times through normal usage, no change.

---

### Post by scrooge_74 on 2009-07-15
Long time since I had to deal with nvidia, check in synaptics see if you need to download any other packages.  Also is the system telling you you could use restricted drivers?

---

### Post by Sweetdaddydong on 2009-07-15
> **scrooge_74 said:**
> Long time since I had to deal with nvidia, check in synaptics see if you need to download any other packages.  Also is the system telling you you could use restricted drivers?

Originally I had the latest driver installed automatically using KDE's Hardware Driver program. It was a snap. The only reason I'm experiencing problems now is because I tried to manually install a new driver from nvidia that would support the CUDA programming language, which would make use of my graphics processor. Thats where everything went wrong. So considering that everything worked before I don't understand why it doesn't work now when I'm using the same program to re-install the original drivers from nvidia. Unless something was deleted when I tried installing the CUDA drivers

---

### Post by scrooge_74 on 2009-07-15
Are you using 9.04 or Hardy? Seems people are having a bunch of problems with new version of drivers

---

### Post by Sweetdaddydong on 2009-07-16
> **scrooge_74 said:**
> Are you using 9.04 or Hardy? Seems people are having a bunch of problems with new version of drivers

I am using Kubuntu 9.04

---

### Post by scrooge_74 on 2009-07-16
I was trying to help a friend last week and we ran into problems with the video cards, I ended installing Hardy on that machine  and the problems got solved

---

