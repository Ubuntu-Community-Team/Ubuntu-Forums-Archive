---
title: "Ubuntu won't boot without monitor plugged in"
date: 2009-07-26
forum: General Help
---

### Post by Vakz on 2009-07-26
I've been searching all night, and found several topics on the matter, but all were 1-2 years old and none seemed to have a solution, but I'm hoping perhaps a fix has been found with the later versions of Ubuntu. 

Here's my problem:
I'm running Ubuntu Server 9.04, and I'm hoping to make it headless. I've installed vnc4server and all that is working just fine, as long as I have a monitor plugged in. Once I remove the monitor however, it won't boot. I read in some other topics that apparently it boots automaticly into low graphics mode, and a window popping up informing about it, but it's hard to "check" it, when i have no monitor/mouse/keyboard plugged in :)

I suppose this is only a problem when using GUI, and in most other topics the OP simply went using CLI instead, but as I'm still fairly new to Linux, I'd prefer having a graphical interface for now.

I suppose you could also wonder why I don't just boot it and then unplug monitor, considering Ubuntu servers rarely needs rebooting, but as the server will not be in my own home, but at a place where powercuts are pretty common, I need it to be a be all on autostart, as the server will be placed at someone who doesn't know the first thing about computers.

Any help is very much appriciated, thanks :)

---

### Post by doug1212 on 2009-07-26
Hi,
I would check the BIOS for "halt on ***" entries and make sure halt on VGA or similar is set to off.

Doug.

---

### Post by Vakz on 2009-07-26
> **doug1212 said:**
> Hi,
I would check the BIOS for "halt on ***" entries and make sure halt on VGA or similar is set to off.

Doug.

Hmm, like I said i'm pretty new, and tbh i have no idea to do what you just said

---

### Post by doug1212 on 2009-07-26
Find the key combination to unlock access the BIOS settings (use Google or handbook) and press them/it while the machine boots then have a look through the entries for something that says halt on VGA or something similar and set it to OFF then save and reboot.
Doug.

---

### Post by Vakz on 2009-07-26
aha, ok. Give me a minute, and i'll see what i can find

Allright, i looked though BIOS (it was probably the most simple BIOS i've ever seen :P )

EDIT1: Couldn't find any mention of "half on", or anything that mentioned VGA. Barely anything about monitor at all, actaully

EDIT2: Allright. I started the computer without monitor plugged in, and the plugged in when it had already booted. What it says is this:

**Ubuntu is running in low-graphics mode.**
The following error was encountered. You may need to update your configuration to solve this.

(EE) NV(0): No valid initial configuration found
(EE) Screen(s) found, but none have a useable configuration.


So evidently, Ubuntu boots. But I need to click ok on the window that pops up, which i of course can't when i don't have a monitor plugged in. Pretty ironic, really.

---

### Post by wojox on 2009-07-26
The computer will still load the GUI. Is there an automatic login option on this vnc4server somewhere? Personally I would just set up ssh and log in through the terminal. There's no better time to learn.

---

### Post by Vakz on 2009-07-26
> **wojox said:**
> The computer will still load the GUI. Is there an automatic login option on this vnc4server somewhere? Personally I would just set up ssh and log in through the terminal. There's no better time to learn.

My problem is that the vnc4server starts AFTER all this "Ubuntu is running in low-graphics mode" and all.

The reason i don't want to have to SSH is as I said, there might be times when the server has to be started by someone who doesn't know anything about computers (since the internet at my own place sucks, i can only get 8/1, it will be at my parents, who have 24/2.5).

As i see it, I either have to make Ubuntu ignore that there is no monitor plugged in, or trick it to think a monitor is plugged in. Either solution is fine. It doesn't have to be a pretty solution, it just has to work.

---

### Post by nikgare on 2009-07-26
You need to edit your xorg.conf file and change the type to vesa.
This works for me, for my headless server (although I'm still stuggling to get the right resolution) - the **vesa** bit is the bit that helps

> Section "Device"
        Identifier      "Configured Device"
        Driver  "vesa"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Device"
        SubSection "Display"
                Depth           24
                Modes           "1024x768"
        EndSubSection
EndSection


---

### Post by Vakz on 2009-07-26
> **nikgare said:**
> You need to edit your xorg.conf file and change the type to vesa.
This works for me, for my headless server (although I'm still stuggling to get the right resolution) - the **vesa** bit is the bit that helps

Thank you! Works perfectly.

I changed it to 1280x800 though (too used to widescreen now :) ), and everything works exactly as i wanted.

---

### Post by stroyeror on 2009-11-12
> **Vakz said:**
> Thank you! Works perfectly.

I changed it to 1280x800 though (too used to widescreen now :) ), and everything works exactly as i wanted.


So where do i add 1280x800

here is the thread i have started about this, also did what nikgare said to do. but dont know where to put 1280x800.

[http://ohioloco.ubuntuforums.org/showthread.php?t=1323120](http://ohioloco.ubuntuforums.org/showthread.php?t=1323120)

---

### Post by Wim Sturkenboom on 2009-11-12
```

Section "Screen"
Identifier "Default Screen"
Monitor "Configured Monitor"
Device "Configured Device"
SubSection "Display"
Depth 24
Modes **"1280x800"** "1024x768"
EndSubSection
EndSection 
```

PS I don't think that the vesa driver supports that resolution

---

### Post by stroyeror on 2009-11-14
> **Wim Sturkenboom said:**
> ```

Section "Screen"
Identifier "Default Screen"
Monitor "Configured Monitor"
Device "Configured Device"
SubSection "Display"
Depth 24
Modes **"1280x800"** "1024x768"
EndSubSection
EndSection 
```PS I don't think that the vesa driver supports that resolution

Adding that to the screen section did not work..

any other ideas?

---

### Post by stroyeror on 2009-11-14
OK i have figured it out 

In the Device section you have to add 
```
Driver "vesa"
```

In the monitor section you have to add
```
HorizSync       28-73
```

Then reboot.

Thats what worked for me.

Below is my xorg.conf

```
# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Device"
    Identifier    "Configured Video Device"
    Option        "UseFBDev"        "true"
    Driver "vesa"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
    HorizSync       28-73
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection
```

---

### Post by paosms on 2009-11-28
Hi to all,

the title of the discussion says it all, i have the same problem BUT with ubuntu 9.10 therefore there is no xorg.conf or gmd.conf. What can i do to have a headless unit? 

I tried to create a xorg.conf "default" file, but all i had at reboot was a weird (because montior kept on flashing) logging in screen (which i didnt have before as i set it to automatic login) and the impossibility to type to actually login! .... I formatted and installed again 9.10.

i've already posted a similar argument in the italian forum , but with no success: nobody seems to know anything about it!

Those who wonder why i re-installed 9.10 rather than 9.04 here is the answer: i did the awful mistake of using ext4. So if i want to use my /home without formating it and lose all my data i have to keep on using 9.10.

Please, help me! There is no sense in having a little server with a huge monitor plugged in!

Thanks,

Andrea

---

### Post by paosms on 2009-11-28
> **stroyeror said:**
> OK i have figured it out 

Below is my xorg.conf

```
# xorg.conf (X.Org X Window System server configuration file)

...

Section "Device"
    Identifier    "Configured Video Device"
    Option        "UseFBDev"        "true"
    Driver "vesa"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
    HorizSync       28-73
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection
```

Hi, what version of ubuntu do you have? because i would try to use your xorg.conf.

I'm currently using 9.10

---

### Post by paosms on 2009-11-28
i solved it, using the first xorg.conf details... Problem is i cant get more than 800x600....

Obviusly i set the xorg file under modes at "1024x768" but it doesent work!

---

### Post by sai0x0x on 2010-06-06
> **paosms said:**
> i solved it, using the first xorg.conf details... Problem is i cant get more than 800x600....

Obviusly i set the xorg file under modes at "1024x768" but it doesent work!

this worked for me. You have do disable  KMS (KernelModeSetting) .  Here you can see how to turn it off for  Intel, Ati,Nvidia: [https://wiki.ubuntu.com/X/KernelModeSetting](https://wiki.ubuntu.com/X/KernelModeSetting)
 

I had to type for my intel graphics chip :
sudo su
echo options i915 modeset=0 > /etc/modprobe.d/i915-kms.conf
 

reboot and done.

---

### Post by manco1911 on 2010-09-05
I just finished configuring my headless home server (AKA: old PC i wanted to give some use).

I followed this post:  [HERE]("http://ubuntuforums.org/showthread.php?p=9807775#post9807775")

Works like a charm now. 

Hope it helps you guys.

---

