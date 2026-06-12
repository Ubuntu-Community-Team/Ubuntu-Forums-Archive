---
title: "Ubuntu slower than Archlinux?"
date: 2004-10-22
forum: General Help
---

### Post by Neo40 on 2004-10-22
Hi,

I have both, Ubuntu and Archlinux on my system. With Archlinux, when I type "glxgears" I get around 1800 FPS. Ubuntu, gives me only 966 FPS!!! 
Why I don't have the same result? 

GeForce2 64Mb
Athlon 1.2Mhz
Nvidia driver

Any idea how to speed up my fps with ubuntu? 

Thanks!

---

### Post by K6-III on 2004-10-22
Make sure that the Nvidia binary drivers are installed prior to testing.

---

### Post by emperor on 2004-10-22
I am getting about 1150 FPS, less than under Arch with Xorg 6.7. As I recall from other installs, there are some Gatos drivers that can speed this up. I have had it running much faster in the past. I have a 1.466 Ghz Athlon XP 1700.

---

### Post by Rancoras on 2004-10-23
Athlon 2800+
512 MB RAM
Geforce FX5200

950 fps @ 1600x1200  75hz

Nothing to compare it to tho?  Is that good or bad?

---

### Post by Mr_Smiley on 2004-10-23
What I think a lot of you haven't done is installed the binary drivers. After installing these you will have proper 3d acceleration. Go here for a howto: [http://wiki.ubuntulinux.org/BinaryDriverHowto](http://wiki.ubuntulinux.org/BinaryDriverHowto)

---

### Post by Neo40 on 2004-10-23
[QUOTE=Mr_Smiley]What I think a lot of you haven't done is installed the binary drivers. After installing these you will have proper 3d acceleration. Go here for a howto: [http://wiki.ubuntulinux.org/BinaryDriverHowto](http://wiki.ubuntulinux.org/BinaryDriverHowto)[/QUOTE]


Ok problem solve! I had installed binary drivers but I forgot to disable GLCore in my /etc/X11/XF86Config-4 file. Now, glxgears gives me 1800 fps!

---

### Post by n3wt on 2004-10-23
Athlon 2800+
512 MB RAM
Geforce FX5200

950 fps @ 1600x1200 75hz



Well, I have an almost Identical setup, and I get around 2200 fps....

---

### Post by Rancoras on 2004-10-23
Yes, I have the binary driver loaded.  I see the nvidia splash when X starts.  I also have the GLCore and DRI lines commented in the X config.  Just for grins I tried with the DRI line uncommented but that had no effect.  Based on n3wt's commect, there must be something wrong with my setup, right?

---

### Post by kensai on 2004-10-25
[QUOTE=Rancoras]Yes, I have the binary driver loaded.  I see the nvidia splash when X starts.  I also have the GLCore and DRI lines commented in the X config.  Just for grins I tried with the DRI line uncommented but that had no effect.  Based on n3wt's commect, there must be something wrong with my setup, right?[/QUOTE]
 I have the same problem I got above 3000 fps inh glxgears using onebaselinux and now I'm having like 2200 fps so is very poored compared to what I've had in other distros. I'd like to see a post explaining this to see how this can be fixed.
Note: I've deleted the lines GLcore and DRI
-thanks

---

### Post by kensai on 2004-10-26
[QUOTE=kensai]I have the same problem I got above 3000 fps inh glxgears using onebaselinux and now I'm having like 2200 fps so is very poored compared to what I've had in other distros. I'd like to see a post explaining this to see how this can be fixed.
Note: I've deleted the lines GLcore and DRI
-thanks[/QUOTE]
 Forget it I see Unreal Tournament is running just fine I think the problem is with glxgears not with the nvidia drivers neither ubuntu.

---

### Post by jdong on 2004-10-26
Clear illustration that Glxgears is for simple OpenGL testing, not comparison benchmarking ;)

---

### Post by Rancoras on 2004-10-26
I see that now, maybe someday there will be something like 3Dmark for linux.

---

### Post by SubCog on 2005-01-20
how do I install ut2k4?

---

### Post by Rancoras on 2005-01-20
That has nothing to do with the topic of this thread....LOL

Go look in the games section, there's a rather lengthy UT thread there and IIRC it has some install pointers. ;)

I'm closing this thread BTW

---

### Post by jdong on 2005-01-20
To finish off: glxgears is designed to be a GLX diagnostic tool. It's not a benchmarking tool.


If you really want to compare, fire up a game and compare the FPS.

---

