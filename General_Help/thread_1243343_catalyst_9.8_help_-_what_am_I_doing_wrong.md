---
title: "catalyst 9.8 help - what am I doing wrong"
date: 2009-08-18
forum: General Help
---

### Post by waspbr on 2009-08-18
k, after banging my head on my table a couple of times I thought it may be better to ask you guys what I have been doing wrong. 

First of all I have downloaded the new 9.8 drivers for my radeon HD 3300 IGP with jaunty 64.

I download the .run file onto the desktop then use the command 

```
sudo sh ./ati-driver-installer-9-8-x86.x86_64.run 

```

the package runs and the ati install window comes up. I select automatic install and the thing just runs by itself. 

at the end of the intallation I run 

```
sudo aticonfig --initial -f

```

then reboot

I login and things are working ok, gnome-do is nice and snappy, this little 3D game called Chromium runs well and so is video playback. 

Then I go to Prefences/Appearance -> Visual effects tab and try to enable normal effects and I get the "Desktop effects could not be enabled" message.

Does Anyone have a clue what I am doing wrong here?

---

### Post by coldReactive on 2009-08-18
Run **compiz** in terminal and paste the output.

---

### Post by waspbr on 2009-08-18
voila
```
Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Checking screen 1Comparing resolution (1680x1050) to maximum 3D texture size (8192): Passed.
Checking for Software Rasterizer: Not present. 
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (core) - Error: Could not acquire compositing manager selection on screen 0 display ":0.0"
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :0.0



```

---

### Post by waspbr on 2009-08-18
maybe it's relevant but here is the output of fglrxinfo 

```
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon HD 3300 Graphics
OpenGL version string: 2.1.8870

```

---

