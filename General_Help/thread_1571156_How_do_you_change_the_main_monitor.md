---
title: "How do you change the main monitor"
date: 2010-09-09
forum: General Help
---

### Post by Kungal on 2010-09-09
I have an external monitor connected to my laptop and I'm trying to change the external monitor to be my main monitor (the one that the menus appear on).

There is no option to change the primary monitor in system>preferences>monitors.

Does anyone know how to do this?

---

### Post by Vigh on 2010-09-09
What graphics card do you have? Generic graphics card drivers do not support setting a primary monitor, you can get around this by simply turning off the monitor you don't want in system preferences monitors and have only 1 monitor but at least it will be displayed on your external monitor. The other option, if you have either an nvidia or ati graphics card is to install the 3d drivers for it, which should allow you to set-up dual-screening properly. If you need help I can advise you on how to install the drivers. If you have an intel graphics card then I am afraid I cannot help as intel do not release drivers for linux.

---

### Post by Kungal on 2010-09-09
It looks like I have an ATI Mobility Radeon HD4570.  If you could tell me how to go about installing those drivers it would be great.

Also, is there no work around for intel graphics cards?  Jusk asking because I have an old computer with an Intel card that I was thinking of installing Ubuntu on.

Thanks

---

### Post by aytech on 2010-09-09
I have the same video card, i've just activated the restricted driver under the Hardware tab and can change dual screeneing both ways. (VGA out &#8594;VGA in)

---

### Post by Vigh on 2010-09-09
quick question 32-bit or 64-bit ubuntu?

[http://support.amd.com/us/gpudownload/Pages/index.aspx](http://support.amd.com/us/gpudownload/Pages/index.aspx)

drivers can be found here

u want to select

notebook graphics
mobility radeon series
HD 4xxx series
linux32bit or 64bit depending on what u have installed (although shouldn't matter as the driver package includes both 32-bit and 64-bit, select the appropriate one just to make sure)

once u have downloaded the file, move it to your /home/user directory

eg. /home/joesmith/

then open a terminal by going to applications, accessories, terminal

type in sudo sh ati-driver-installer-10-8-x86.x86_x64.run

follow the prompts like you would any normal installation
reboot, and you should have 3d graphics acceleration enabled and also the option to set your dual-screen primary device in the ati menu

try testing out your graphics by installing nexuiz- a 3d 1st person shooter linux game, big download, but fantastic graphics

regarding your intel computer, you can use generic open-source intel graphics drivers, if it is an old computer i suggest using XUBUNTU 10.04 although i have never used it myself, it is a cut-down version of ubuntu, so should support intel graphics well, while running on an old computer

---

### Post by Kungal on 2010-09-09
Awesome,

Thanks for the detailed instructions.  It works perfectly now.  

I'll get on to that game a bit later on and also give the Intel drivers a try.

Thanks again

---

