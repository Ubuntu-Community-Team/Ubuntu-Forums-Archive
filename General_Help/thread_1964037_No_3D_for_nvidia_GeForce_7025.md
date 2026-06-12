---
title: "No 3D for nvidia GeForce 7025"
date: 2012-04-23
forum: General Help
---

### Post by Docaltmed on 2012-04-23
Upgraded to 12.04 recently, but I cannot get either Unity 3D nor Gnome Shell to run. Unity 2D works fine. 

```
~$ /usr/lib/nux/unity_support_test -p
OpenGL vendor string:   NVIDIA Corporation
OpenGL renderer string: GeForce 7025 / nForce 630a/integrated/SSE2
OpenGL version string:  2.1.2 NVIDIA 295.40

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity 3D supported:       yes
```

I've added the x-swat/x-updates PPA, and updated, but there were no new drivers, so I assume I'm using the most recent nvidia drivers.

Suggestions?

---

### Post by bogan on 2012-04-23
Hi!, **docaltmed**, 

There have been problems with the 295.40 driver with GeForce 7xxx & 8xxx series nvidia video cards, acknowledged by NVIDIA, since APRIL 12th. 
For some, version 295.33 or 295.20 have proved a cure, or at least an improvement, partly dependant on whether a slow-down or hang-up crashes are the symptoms.

Others have had to regress to 290.10.

If you run:```
 sudo nvidia-installer --latest
``` from a text terminal; ie. boot to a tty, or first run:```
  sudo service lightdm stop 
```from a GUI terminal, it will tell you what version will be installed with:```
sudo nvidia-installer -f
```Then reboot:  which also uninstalls the existing version which is essential to do if you use a different method.

Currenly, although 295.40 is the latest offered, the above will actually offer and install 295.33.

Chao!, **bogan.**

---

### Post by Docaltmed on 2012-04-23
bogan, thanks for the suggestions! I downgraded to .33, and that turned into a trainwreck; I couldn't get past an "out of range" error on the monitor.

So I ssh'ed in from another computer, re-downloaded .40, and reinstalled it. I'm back to Ubuntu 2D only, but at least that's something.

Thank you very much for the suggestion. At least now I know what the problem is. I guess I'll just have to wait until NVIDIA gets its act together.

---

### Post by Mr.Dunham on 2012-06-17
> **Docaltmed said:**
> I couldn't get past an "out of range" error on the monitor.

I know this post is a few months old, but that "out of range" error on the monitor has got a pretty easy solution here:
[http://ubuntuguide.org/wiki/Ubuntu:Precise#Frequency_Out_of_Range_.2F_Choose_New_Resolution](http://ubuntuguide.org/wiki/Ubuntu:Precise#Frequency_Out_of_Range_.2F_Choose_New_Resolution)

---

