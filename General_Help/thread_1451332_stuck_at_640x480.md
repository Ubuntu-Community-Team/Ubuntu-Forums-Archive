---
title: "stuck at 640x480"
date: 2010-04-10
forum: General Help
---

### Post by dd1linux on 2010-04-10
Well, I have been using linux for about a year and a half.  I am able to troubleshoot alot of problems by myself, but not this one.  First I'll give a quick summary, then the second paragraph will have more detail:

1.) Basically I am stuck at 640x480 res all of sudden even though I have been using restricted driver forever.  It shows I am still using the nvidia driver, and xsettings are there and everything.  but I can't up my resolution.

2.) I have had two monitors plugged in forever using a triple boot windows (vista and 7) and ubuntu (I only used the second monitor for windows).  One day I unplugged the 2nd monitor, and all of a sudden windows 7 was messed up looking, so I disabled SLI and then went to ubuntu.  It was stuck at 640x480! I tried changing all the settings I could, but eventually gave up and decided to re-install ubuntu.  Once I installed the restricted drivers, the SAME thing happened!  I don't get it, I had everytihng working fine for a year, then all of a sudden this.  It's not possible that the VGA cable is the problem is it??  Please let me know if you need more info. I am horrible at explaining this.

Device specs:
triple boot (ubuntu, windows 7,windows vista)
amd phenom 8550 64bit
2G ram
DUAL nvidia 8600GT 

BTW: even though I have a 64 bit machine, I use 32 bit ubuntu.  Also, I dont think this is a hardware problem b/c windows vista still looks perfect.

Any help would be greatly appreciated!

---

### Post by motsteve on 2010-04-10
I've had this problem before also it is usually caused by a hosed xorg.conf file in your /etc/X11 directory.  There supposedly is a way to regenerate the xorg.conf file, but it has never worked for me.  Everytime, I usually just putzed around and get it working and then forgot what I did so that I could write it all down.:(

You might try: $ dpkg -reconfigure xserver-xfree86.  

(I hope it works for you because that's the only reply to my problem that I got from the forums and it didn't work the times I tried it, but everyone said that it HAD to have worked.)

---

### Post by dd1linux on 2010-04-10
thx steve, ill go give it a shot.

-------------------------------------

No luck here either, Steve!

---

### Post by dd1linux on 2010-04-11
Please, anymore suggestions??

---

### Post by Stenrad on 2010-04-11
Hi there!

Have you tried running the following?

```
sudo nvidia-xconfig
```

Hope that helps!

---

### Post by dd1linux on 2010-04-12
Yes, I had tried that Stenrad.  I just re-installed ubuntu, but I am not going to install the nvidia driver, until i understand how to get back to this default setting I am at now.  At least it is tolerable (1152x864).  Can you tell me how to go back should things fail, all i know how to do is nano the xorg file to use vesa driver if things go haywire, but it's always only 800x600 (with no option to go higher), so im basically screwed at that point.  If I am not giving enough info, someone please let me know what I need to post.

---

### Post by Pjotr123 on 2010-04-12
You might try this:

- install the restricted driver from Nvidia in the usual way (System - Administration - Hardware drivers)

- then in the terminal:
```
gksudo nvidia-settings
```

Press Enter.

In this config app, do the following:

- Click on "X Server Display Configuration"

- Click on tab "Display" (probably open already)

- Resolution: click on the pointer button next to "Auto"

- Choose the resolution you want

- Click on "Save to X Configuration File"

- Click on Close

- Do a full reboot. Now the resolution should be right.

---

### Post by dd1linux on 2010-04-12
the only two options it gives me for res. is 640x480 and 320x240.  Also, for further information, everytime I run xconfig I have to manually edit the device section to include busid  "PCI:04:0:0", because I have two video cards, and it always defaults to the other one i guess. I know the 04 tells it the PCI bus, but why the 0:0?  perhaps if I change to PCI:04:0:1 that might help?  Someone please help!

---

### Post by dd1linux on 2010-04-13
Well, trying to change around the Busid didn't help either.  I even went and installed the 64-bit version, and tried those drivers with no luck.  Does anyone think this could be an SLI related problem? Should I remove the bridge, or maybe on of the cards and the bridge?  It worked fine for over a year, but maybe it's worth a shot.  I await replies.

---

### Post by dd1linux on 2010-04-13
problem solved!!!  I simply installed a different OS (PCLinuxOS in my case), enabled the nvidia drivers, and then copied it's xorg.conf (which included much more information, and accurate information at that!)  Then I reinstalled ubuntu, enabled the restricted drivers, and copied the xorg.conf from PCLinuxOS to /etc/X11/.  I believe the problem came from ubuntu not detecting my monitor correctly. I hope this helps someone in the future.

---

### Post by JoelOl75 on 2010-04-14
I wish there was an online xorg.cong file generator for Ubuntu which doesn't use one by default.  I believe they are trying to autoconfigure everything to just work, but in many cases it just doesn't.  Even my laptop (Nvidia Quadro FX3500M) the graphics are fine but the touchpad (Alps) needs so much xorg.conf setting that I always keep a backup from the fiesty days just to cut that section out and hack together a working xorg.conf.


Can be frustrating when you don't have a template to work from.

---

