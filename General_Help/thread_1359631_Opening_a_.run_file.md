---
title: "Opening a .run file"
date: 2009-12-19
forum: General Help
---

### Post by Marksman09 on 2009-12-19
Hey guys,

Sorry if this is in the wrong section but I'm new to the forums and Linux, and I'm gonna kill myself soon if I dont get help. After downloading the drivers linux recomended for my 9500gt and rebooting I got a message saying there was a problem with the choice to run in low graphics as a 1 off. I downloaded new drivers for linux off the nvidia website but it came as a .run file and it keeps opening in gedit. After 30-40 minutes of googling how to simply open a run file I gave up. Please help!

Thanks,
Mark

---

### Post by 3rdalbum on 2009-12-19
> **Marksman09 said:**
> Hey guys,

Sorry if this is in the wrong section but I'm new to the forums and Linux, and I'm gonna kill myself soon if I dont get help. After downloading the drivers linux recomended for my 9500gt and rebooting I got a message saying there was a problem with the choice to run in low graphics as a 1 off. I downloaded new drivers for linux off the nvidia website but it came as a .run file and it keeps opening in gedit. After 30-40 minutes of googling how to simply open a run file I gave up. Please help!

Thanks,
Mark

In order to install the Nvidia driver from [www.nvidia.com](www.nvidia.com) you need to temporarily turn off the X server, which leaves you with a command-line only for a short while.

There are HOWTOs about how to do that, but a better bet for you would be to install the "envy-ng" program (from Synaptic) and run it; it should download and install the latest driver for you from the Nvidia website.

---

### Post by orlox on 2009-12-19
This is copied from [here]("http://ubuntuforums.org/showthread.php?t=1100986&page=2")

1) Login as normal.
2) Change to runlevel 3 with ctrl+alt+F1 ( if you open a terminal within gnome, it will disappear after running the next command)
3) sudo /etc/init.d/gdm stop
4) sudo -i
5) cd to/directory/with/the/run/file
6) chmod +x <run-file>
7) sh <file> (specifically for Nvidia cause it doesn't know the .run is a shell script)
 Follow instructions.
9) sudo /etc/init.d/gdm start

Be sure to understand all the points before trying this, and be aware that after ctrl+alt+F1 a terminal will take over your desktop.

---

### Post by orlox on 2009-12-19
> **3rdalbum said:**
> In order to install the Nvidia driver from [www.nvidia.com](www.nvidia.com) you need to temporarily turn off the X server, which leaves you with a command-line only for a short while.

There are HOWTOs about how to do that, but a better bet for you would be to install the "envy-ng" program (from Synaptic) and run it; it should download and install the latest driver for you from the Nvidia website.

I believe that since some time ago, envy-ng uses the packages from the repos, not the original ones from nvidia.

---

### Post by Marksman09 on 2009-12-20
Okay, I tried the envy-ng option and I tried doing it through terminal but it still cant pick up my graphics card. I'm still getting the message on startup but now i get something about failing to load something.

---

### Post by pbrane on 2009-12-20
Have you tried 
```

sudo dpkg-reconfigure -phigh xserver-xorg

```
in a terminal?

This should get you back to a default condition. From there you can try again. If you use **envyng -t** that will get you the latest driver from the repos. I think it is still at 185.

There is also this thread:
[http://ubuntuforums.org/showthread.php?t=57368]("http://ubuntuforums.org/showthread.php?t=57368")

---

