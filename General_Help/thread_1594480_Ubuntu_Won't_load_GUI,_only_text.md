---
title: "Ubuntu Won't load GUI, only text?"
date: 2010-10-12
forum: General Help
---

### Post by Woofington on 2010-10-12
First off I have never been too great with Ubuntu but I have been using it for several years now.  I had 10.04 and upgraded to 10.10 last night.  The installation and download all went smooth and there were no errors.  It asked me to restart and I did but now it is acting funky.

Instead of loading my new 10.10 normally it leaves me at a text screen where it says:

"lucian-laptop login:"
its basically a command line prompt.  I can enter my credentials, it will then ask me for my password, and then it leaves me at this:

"Welcome to Ubuntu!
* Documentation:  [https://help.ubuntu.com/](https://help.ubuntu.com/)

0 packages can be updated
0 updates are security updates

lucian@lucian-laptop:`$ "

I can type in commands at this point but I don't have any idea what to do.  I just want to get to my normal GUI and use it like I normally use it.  I need this laptop for school so this problem is quite crippling at the moment.

And my laptops names is "lucian-laptop" and my username is lucian, not that you guys didn't already figure that out :P

Any help would be greately appreciated, again I am not too great at this.

edit:  Oh I tried booting in recovery mode and it will get to the point where it will ask me what to do and if I say resume it just dumps me back to the prompt.  

Also once it did a disk check and then again after completing this dumped me back to the prompt.  

If I shut it down I at least see that pretty splash shut down logo.

---

### Post by Rubi1200 on 2010-10-12
At the prompt try ```
startx
``` (may require the use of sudo) or ```
sudo /etc/init.d/gdm start
```See if that helps.

---

### Post by Woofington on 2010-10-12
> **Rubi1200 said:**
> At the prompt try ```
startx
``` (may require the use of sudo) or ```
sudo /etc/init.d/gdm start
```See if that helps.

I get this:

"Fatal server error:
AddScreen/ScreenInit failed for driver 0

Please consult the X.org Foundation support 
at [http://wiki.x.org](http://wiki.x.org)
for help
Please also check the log file at "/var/log/Xorg.0.log" for additional information

ddxSigGiveUp: Closing log
giving up
xinit: no such file or directory (errno 2): Unable to connect to X server
xinit: No such process (errno 3):  Server error"

and then I am back at that prompt again.

edit:  Whoops and this above the previous stuff:

(EE) intel(0): Failed to allocate framebuffer.
(EE) intel(0): couldn't allocate initial framebuffer.

---

### Post by Woofington on 2010-10-12
Anyone know how to help me?  I need it for class today.

---

### Post by Woofington on 2010-10-12
Someone must know!

---

### Post by feroxy on 2010-10-12
if you have an older nvidia graphics card, it could be due to this [https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/626974](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/626974) 
The only thing that has worked for me at this point is to edit the /etc/X11/xorg.conf and change the driver to "nv" (you could also try "nouveau" but it didn't work for me)

---

### Post by Woofington on 2010-10-12
> **feroxy said:**
> if you have an older nvidia graphics card, it could be due to this [https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/626974](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/626974) 
The only thing that has worked for me at this point is to edit the /etc/X11/xorg.conf and change the driver to "nv" (you could also try "nouveau" but it didn't work for me)

How do I edit that?  What command should I use?

---

### Post by feroxy on 2010-10-12
Be sure you have one of the above graphics card. I only give these instructions in that case.

backup the original file:

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup

then

sudo nano /etc/X11/xorg.conf

find section "device", and change Driver from "nvidia" to "nv" (or try "nouveau" which is preferred if it works for you). control-o to save, then control-x to exit. And reboot. 
Hopefully that will get you up and running in a gui (albeit slower and probably glitchier than before). Keep an eye on that bug report to check when the nvidia drivers get updated and re-enable them "administration/additonal drivers" when they are.

---

### Post by Woofington on 2010-10-12
> **feroxy said:**
> Be sure you have one of the above graphics card. I only give these instructions in that case.

backup the original file:

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup

then

sudo nano /etc/X11/xorg.conf

find section "device", and change Driver from "nvidia" to "nv" (or try "nouveau" which is preferred if it works for you). control-o to save, then control-x to exit. And reboot. 
Hopefully that will get you up and running in a gui (albeit slower and probably glitchier than before). Keep an eye on that bug report to check when the nvidia drivers get updated and re-enable them "administration/additonal drivers" when they are.

I don't even have a viarable for driver:

"Section "Device"
  Identifier "Configured Video Device"
EndSection"

That's all I have.  There are sections for Monitor, and Screen above it.

---

### Post by feroxy on 2010-10-12
> **Woofington said:**
> I don't even have a viarable for driver:

"Section "Device"
  Identifier "Configured Video Device"
EndSection"

That's all I have.  There are sections for Monitor, and Screen above it.

Hmm. Different from mine then. I did otherwise encounter the exact same situation that you describe after the upgrade since I had the nvidia proprietary driver installed. but my device section looked like

```
Section "Device"
        Identifier      "Default Device"
        Driver  "nvidia"
        Option  "NoLogo"        "True"
EndSection
```

---

### Post by feroxy on 2010-10-12
I have read advice elsewhere to just remove the xorg.conf altogether and reboot. _If you have made a backup already_, you could try that.

sudo rm /etc/X11/xorg.conf

if it doesn't work you can restore your original by

sudo cp /etc/X11/xorg.conf.backup /etc/X11/xorg.conf

---

### Post by Woofington on 2010-10-12
> **feroxy said:**
> Hmm. Different from mine then. I did otherwise encounter the exact same situation that you describe after the upgrade since I had the nvidia proprietary driver installed. but my device section looked like

```
Section "Device"
        Identifier      "Default Device"
        Driver  "nvidia"
        Option  "NoLogo"        "True"
EndSection
```

Thanks I added the driver option and tried nvidia nv and nouveau.  All three change the fatal server error:
"no screens found"
This is frustrating :(
Can you post your whole xorg.conf?

---

### Post by feroxy on 2010-10-12
> **Woofington said:**
> Thanks I added the driver option and tried nvidia nv and nouveau.  All three change the fatal server error:
"no screens found"
This is frustrating :(
Can you post your whole xorg.conf?

```


Section "Screen"
    Identifier    "Default Screen"
    DefaultDepth    24
EndSection

Section "Module"
    Load    "glx"
EndSection

Section "Device"
    Identifier    "Default Device"
    Driver    "nv"
    Option    "NoLogo"    "True"
EndSection


```

This is only going to work if you have older nvidia hardware. Do you know for sure if you do? or if it is nvidia at all?

---

### Post by Woofington on 2010-10-12
Thank you for all your help feroxy

Solved the issue completely.  

here is what I did:

sudo xorg -configure

which created this new xorg.conf file:  xorg.conf.new in the root directory.
tested it with:

sudo xorg.conf.new -config -retro

it works so I:

sudo cp xorg.conf.new /etc/X11/xorg.conf

Then just did startx and it started!  :D

So I guess it just didn't configure properly for some reason.

---

### Post by feroxy on 2010-10-12
glad to hear it's sorted :)

---

### Post by enthralledunixuser on 2011-02-23
I just solved this problem with my machine I did happen to have an old nvidia graphics card a 8760 as best I can recall. I have no idea if this will help anyone, but I thought I would comment none the less.

I was cruising along playing with stuff, being excited, when I noticed that there was an issue with my sound so naturally I went to look for unloaded/outdated sound drivers for my sound card and in the process I reloaded a graphics driver thinking maybe it was an issue with compatibility. I thought nothing of it until I rebooted and then I was suddenly without a GUI.

Long story short I loaded an older driver and activated the nvidia bug, btw thank you feroxy, "nouveau" didn't work but "nv" did at least to access my root. Then I reloaded the most recent driver problem solved.

Anyways something to beware of maybe it will help you...

cheers

---

