---
title: "can not change screen resolution"
date: 2005-02-17
forum: General Help
---

### Post by jamaas on 2005-02-17
I've just loaded hoary and it seemed to set up fine, now when I reboot the only resolution I have available to me is 640x480 .... bad.

I tried using the gui in hoary to change it, no luck.

I also ran
sudo dpkg-reconfig xserver-xorg 
but no luck.

Have I done something wrong.  New computer, Sapphire (ati) radeon graphics card and NEC lcd 1770 monitor so lots of choices here.

I'm a newbie so please go slow... :-)

Thanks

Jim

---

### Post by Xian on 2005-02-17
[QUOTE=jamaas]I've just loaded hoary and it seemed to set up fine, now when I reboot the only resolution I have available to me is 640x480 .... bad.[/QUOTE]
Hoary uses xorg, right? I think that is correct.
If so the file should be found in a path similar to: /etc/X11/xorg.conf

Try editing the Xconfig file directly and see if that helps. For example, if you want a 1024x768 resolution then you want your xorg.conf file to look similar to the example below in the  "Screen" section. The only relevant line is the one that matches your DefaultDepth preference. In the case presented it is "24", so X will attempt to load the settings for that initially. The resolution listed first in the "Modes" line is considered the default. Put your preference there and the others are to be considered only alternates.

```
sudo gedit /etc/X11/xorg.conf
```
```
Section "Screen"
  DefaultDepth 24
  SubSection "Display"
    Depth      15
    Modes       "1024x768" "800x600" "640x480" 
  EndSubSection
  SubSection "Display"
    Depth      16
    Modes      "1024x768" "800x600" "640x480" 
  EndSubSection
  SubSection "Display"
    Depth      24
    Modes       "1024x768" 800x600" "640x480" 
  EndSubSection
  SubSection "Display"
    Depth      32
    Modes      "1024x768" "800x600" "640x480" 
  EndSubSection
  SubSection "Display"
    Depth      8
    Modes      "1024x768" "800x600" "640x480" 
  EndSubSection
```

---

### Post by jamaas on 2005-02-18
Thanks Xian,

I tried this edit, rebooted and still no luck.

I'm not having a rant at you, but this is quite rediculous.  How can a system, run from a live disk, set itself up properly, and then you go and install it and it works fine until you reboot.  This is just nonsense.   And then non one seems to know of a utility to run or a file to fix to correct it!

I spend to much time just trying to get Ubuntu to do the very very basics, might well be time for a switch.

Thanks for your help.

Jim 
[QUOTE=Xian]Hoary uses xorg, right? I think that is correct.
If so the file should be found in a path similar to: /etc/X11/xorg.conf

Try editing the Xconfig file directly and see if that helps. For example, if you want a 1024x768 resolution then you want your xorg.conf file to look similar to the example below in the  "Screen" section. The only relevant line is the one that matches your DefaultDepth preference. In the case presented it is "24", so X will attempt to load the settings for that initially. The resolution listed first in the "Modes" line is considered the default. Put your preference there and the others are to be considered only alternates.

```
sudo gedit /etc/X11/xorg.conf
```
```
Section "Screen"
  DefaultDepth 24
  SubSection "Display"
    Depth      15
    Modes       "1024x768" "800x600" "640x480" 
  EndSubSection
  SubSection "Display"
    Depth      16
    Modes      "1024x768" "800x600" "640x480" 
  EndSubSection
  SubSection "Display"
    Depth      24
    Modes       "1024x768" 800x600" "640x480" 
  EndSubSection
  SubSection "Display"
    Depth      32
    Modes      "1024x768" "800x600" "640x480" 
  EndSubSection
  SubSection "Display"
    Depth      8
    Modes      "1024x768" "800x600" "640x480" 
  EndSubSection
```[/QUOTE]

---

### Post by hashimoto on 2005-02-18
Shouldn't it be:
sudo dpkg-reconfigure...?

---

### Post by jamaas on 2005-02-18
Thanks Hashimoto,

Yes that part seems to work, but I need to tell it exactly what package ... so what package do I need to reconfigure??

Thanks

Jim

[QUOTE=hashimoto]Shouldn't it be:
sudo dpkg-reconfigure...?[/QUOTE]

---

### Post by Panos on 2005-02-18
[QUOTE=jamaas]I've just loaded hoary and it seemed to set up fine, now when I reboot the only resolution I have available to me is 640x480 .... bad.

I tried using the gui in hoary to change it, no luck.

I also ran
sudo dpkg-reconfig xserver-xorg 
but no luck.

Have I done something wrong.  New computer, Sapphire (ati) radeon graphics card and NEC lcd 1770 monitor so lots of choices here.

I'm a newbie so please go slow... :-)

Thanks

Jim[/QUOTE]

Hi jamaas

I had the same problem (in Warty AMD64) and I solved it by entering the exact frequencies of my monitor (LG TFT 1715s). You should enter the exact horizontal and vertical frequencies of your monitor in the relative section of the xorg.config file (I did that in the XF86Config-4 file, but their structure is the same), and the X server most propably will correctly recognize your monitor's resolutions.

Cheers

Panos

---

### Post by Xian on 2005-02-18
[QUOTE=jamaas]I'm not having a rant at you, but this is quite rediculous.  How can a system, run from a live disk, set itself up properly, and then you go and install it and it works fine until you reboot.  This is just nonsense.   And then non one seems to know of a utility to run or a file to fix to correct it![/QUOTE]
jamass, any "utility" that you may find will be doing exactly what I am helping you with, which is to edit the xorg.conf file. There is no difference, but this way you can actually see what is taking place and learn how and why your system works in the manner that you have described. If the adjustments I suggested you make did not work, I would have asked you to post the entire xorg file and then probably looked next at the resolution settings. This is just how I do things in Linux -- I go to the source and fix the problem where it lives. But hey, to each his or her own.

As to your second comment, there are honestly a multitude of reasons why your installed "look and feel" will differ substantially from a LiveCD. It obviously is not the most desirable outcome to to certain, but that is just how technology often behaves, which is to say not always on a expected or optimal path.

---

### Post by Buffalo Soldier on 2005-02-18
[QUOTE=jamaas]Thanks Hashimoto,

Yes that part seems to work, but I need to tell it exactly what package ... so what package do I need to reconfigure??

Thanks

Jim[/QUOTE]

sudo dpkg-reconfigure xserver-xorg

---

### Post by grj on 2005-02-18
In the xorg.conf check to see what driver is being used. If it is correct, verify that the driver is being loaded. You can do that with

lsmod | grep ati
or
lsmod

If an ati driver is listed

modprobe <driver name> 

Sorry, I do not know what the driver name is for ati cards.

---

