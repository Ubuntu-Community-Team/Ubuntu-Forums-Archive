---
title: "log in window wrong resolution"
date: 2009-11-11
forum: General Help
---

### Post by defenestratos on 2009-11-11
Hello,

Can anyone help me find a way to change the resolution in the log in window?

When installed, Ubuntu detects my screen resolution as 1600x1200 or something. Unfortunately my screen is 1024x768 and that means that a large amount of the workspace is invisible on the right and bottom sides of my physical screen. 
Once logged in I am able to change the resolution to the correct one (1024x768) albeit with an impossible 0hz refresh rate. This is a permanent fix.
The problem is that in the login window I still have the old huge resolution and it is very ugly with compromised usability. 
If anyone can help me it would be good!

BENQ Joybook R23
Karmic 64

Can anyone help me find a way to change the resolution in the log in window?

Thanks in advance!!!

---

### Post by defenestratos on 2009-11-15
Does no one know what my problem is? No one has given me any pointers. I know it isn't a crippling problem but it is still important for me and the community. 
Please help:)

---

### Post by defenestratos on 2009-11-15
My graphics card.

> hugo@hugo-laptop:~$ lspci | grep VGA
01:00.0 VGA compatible controller: VIA Technologies, Inc. K8M800/K8N800/K8N800A [S3 UniChrome Pro] (rev 01)


lshw excerpt

>            *-display UNCLAIMED
                description: VGA compatible controller
                product: K8M800/K8N800/K8N800A [S3 UniChrome Pro]
                vendor: VIA Technologies, Inc.
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 01
                width: 32 bits
                clock: 66MHz
                capabilities: pm agp agp-3.0 bus_master cap_list
                configuration: latency=128 mingnt=2
                resources: memory:a4000000-a7ffffff(prefetchable) memory:e1000000-e1ffffff memory:a0000000-a000ffff(prefetchable)


Does this mean that my graphics card is unrecognized by the kernel?

---

### Post by arnab_das on 2009-11-15
download "startupmanager" and change the resolution.

---

### Post by defenestratos on 2009-11-15
trying

---

### Post by defenestratos on 2009-11-15
I tried Startupmanager and it didn't do anything to my login screen. It is still too massive to fit onto my screen. I adjusted the only resolution dialog I could but that was for the boot loader so Grub looks all swish with 1024x768.

My problem is still the same: The phase of graphics which includes the login screen is in the wrong resolution. Both the boot screen and the logged in user environment are correct (1024x768).

I can't seem to find Xorg and I understand that 9.10 does things a bit differently.
Thanks for the answer!

---

### Post by defenestratos on 2009-11-20
I'm frustrated because no one is commenting on my post. Have I put it somewhere inappropriate? I have received one answer. I feel like I am having a dialog with myself. 

It would mean a lot if someone were to give me their expertise because I'm out of ideas.

---

### Post by nomenklatura on 2009-11-20
try this:

[http://www.rushmessageboard.com/cpmb/index.php?showtopic=33283](http://www.rushmessageboard.com/cpmb/index.php?showtopic=33283)

it unfortunately doesn't work for me...

---

### Post by binaryloop on 2009-11-27
I'm having the same issue (as well as others) with the S3 Unichrome chipset. I've been reading threads here:

[http://ubuntuforums.org/showthread.php?t=1079314](http://ubuntuforums.org/showthread.php?t=1079314)
[http://ubuntuforums.org/showthread.php?t=1190554](http://ubuntuforums.org/showthread.php?t=1190554)
[https://help.ubuntu.com/community/OpenChrome](https://help.ubuntu.com/community/OpenChrome)

To try to fix it. But, no luck yet. (Just lots of reboots to try new X settings).

I'm half tempted to just go out and buy a new Nvidia card. ;)

---

### Post by defenestratos on 2009-11-27
Thanks for the answer! I was starting to feel lost in the woods. I will try that stuff when I get back home later.
How did you find that stuff? I googled my *** off!
H

---

### Post by defenestratos on 2009-12-20
Found out how to change the resolutions.
1) Stop GDM
sudo /etc/init.d/gdm stop
2)sudo xorg -configure
3)sudo gedit /home/hugo/xorg.conf.new
4)Paste > Section "Monitor"
    Identifier "Monitor0"
    VendorName "Monitor Vendor"
    ModelName "Monitor Model"
    HorizSync 31.5 - 50
    VertRefresh 50-110
EndSection
Section "Screen"
    Identifier "Screen0"
    Device     "Card0"
    Monitor    "Monitor0"
    SubSection "Display"
        Depth        1
        Viewport 0 0
        Modes      "1024x768"
    EndSubSection
    SubSection "Display"
        Depth        4
        Viewport 0 0
        Modes      "1024x768"
    EndSubSection
    SubSection "Display"
        Depth        8
        Viewport 0 0
        Modes      "1024x768"
    EndSubSection
    SubSection "Display"
        Depth        16
        Viewport 0 0
        Modes      "1024x768"
    EndSubSection
    SubSection "Display"
        Depth        24
        Viewport 0 0
        Modes      "1024x768"
    EndSubSection
EndSection
5)Copy xorg.conf.new to /etc/X11/xorg.conf (remove .new from file name)
Worked for me anyway. Many thanks to [www.rushmessageboard.com](www.rushmessageboard.com)

---

