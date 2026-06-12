---
title: "My computer sleeps and dont wake up then"
date: 2009-08-05
forum: General Help
---

### Post by miros84 on 2009-08-05
Hello. I have terrible problems with my ubuntu. I have it in standby for 20 minutes. After 20 minutes my monitor is off, but when I press some key its impossible to wake up my computer again. I must do hard reset. Thats horrible. My video card is nvidia.
Can somebody help me with that?

---

### Post by ppirilla on 2009-08-05
I'm not sure how to fix it, but i'm sure that whoever can solve your trouble will find it easier if you tell us what version of ubuntu you're running.  Is the problem on a fresh installation, or did it develop?

As a guess, try pressing the power button to wake it?

---

### Post by miros84 on 2009-08-05
I have ubuntu 9.04
I press power button and nothing.

---

### Post by warp99 on 2009-08-05
With Nvidia cards you may need to add the following line:

```
Option "NvAGP" "2"
```

to the "Device" section of your xorg.conf. This is sometimes needed even if your system does not use AGP.

---

### Post by miros84 on 2009-08-05
Can you explain me better how can I add that? In which file? And where is it?

---

### Post by warp99 on 2009-08-05
> **miros84 said:**
> Can you explain me better how can I add that? In which file? And where is it?

Now adding the NvAGP option depends on if you're using the proprietary modules from Nvidia otherwise these changes will have absolutely no effect.

First make a backup of your xorg.conf file:

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.backup
```

Then open the file in a text editor:

```
sudo gedit /etc/X11/xorg.conf
```

Scroll down to this section or something similar:

```
Section "Device"
	Identifier	"nVidia Corporation [GeForce 9500]"
	Boardname	"NVIDIA GeForce 9 Series"
	Driver		"nvidia"
	Option          "NoLogo" "True"
EndSection

```

And add the additional option:

```
Section "Device"
	Identifier	"nVidia Corporation [GeForce 9500]"
	Boardname	"NVIDIA GeForce 9 Series"
	Driver		"nvidia"
	Option          "NoLogo" "True"
       Option          "NvAGP"  "2"
EndSection
```

Save the file then logout and login to see if this helps. Another issue may be if you have the "cool and quiet" option enabled in you computer BIOS. Sometimes this is a problem with the Nvidia modules so you need to disable it.

---

### Post by miros84 on 2009-08-06
Thank you very much. I will try it and I will tell you if that works for me. :D

---

### Post by miros84 on 2009-08-06
I added this line.
I still have this problem.
My nvidia driver is propietary

---

### Post by warp99 on 2009-08-06
What's the make/model of the computer (or motherboard if the machine is home built) and the video card? This may be a specific problem with your combination and/or video card setup. 

BTW nvidia is notorious for this problem. I've had many problems with the proprietary drivers not allowing the computer to wake from suspend, but eventually I solved all the issues on my machines.

---

