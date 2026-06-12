---
title: "Problems with Ubuntu and LCD HDTV"
date: 2009-07-06
forum: General Help
---

### Post by santellan17585 on 2009-07-06
I recently decided to save some space in my room by investing in a media keyboard and connecting my PC to my LCD HDTV and all is working fine...except my Ubuntu. I have my PC triple booting with Ubuntu, Windows XP Pro, and Windows Vista Ultimate with Ubuntu being my primary OS and when I try to use it on the LCD TV, it reports display errors. Says something about no available configuration. Works fine with my LCD Monitor, but no dice with the TV. 

The TV is lower resolution than my regular monitor (Regular Monitor 1440 x 900, HDTV 1366 x 768, so I tried lowering the resolution while connected to my old monitor and connecting the TV while the machines was still on and setting it to the correct resolution and it worked fine. However, as soon as I rebooted, I had the issues all over again. 

I also tried reinstalling Ubuntu, but the was a no go as well. Any ideas? My TV is a 1080p Vizio 32in. LCD HDTV with my PC connected via VGA connection and I am running Jaunty Jackalope fully updated. 

Thanks!

---

### Post by elitenoobboy on 2009-07-06
> **santellan17585 said:**
> 
I also tried reinstalling Ubuntu, but the was a no go as well.

Does it display correctly using just the live cd?

---

### Post by santellan17585 on 2009-07-06
> **elitenoobboy said:**
> Does it display correctly using just the live cd?

I actually have not tried that as I usually install Ubuntu using Wubi, but I will have to give that a try when I get home.

---

### Post by agathian on 2009-07-06
Which version of Ubuntu are you running?

I use my laptops ( one running hardy, the other running Jaunty) with my 37" samsung LCD,(typically when i want to watch videos), without any issues. Typically if i boot it up when connected to LCD, it auto detects the supported resolutions and comes up properly.  Alternately, i can also use the display preferences or NVIDIA X settings to switch to the LCD, if i connect it after backup.

---

### Post by santellan17585 on 2009-07-07
I am running 9.04 Jaunty Jackalope. Tried the Live CD with the same errors.

---

### Post by agathian on 2009-07-08
Santellan,

What you are looking for should work out of the box. Do you have this problem just when booting up with Ubuntu or with other OSs as well?

If you intend to use the LCD TV as your primary monitor, then you could probably lock down the available resolutions to X - check this out for reference [https://answers.launchpad.net/ubuntu/+question/16439]("https://answers.launchpad.net/ubuntu/+question/16439").

Make a copy of xorg.conf, or any other file you are changing, and so that you can rollback if it doesnt work.

Good luck!

---

### Post by santellan17585 on 2009-07-08
> **agathian said:**
> Santellan,

What you are looking for should work out of the box. Do you have this problem just when booting up with Ubuntu or with other OSs as well?

If you intend to use the LCD TV as your primary monitor, then you could probably lock down the available resolutions to X - check this out for reference [https://answers.launchpad.net/ubuntu/+question/16439](https://answers.launchpad.net/ubuntu/+question/16439).

Make a copy of xorg.conf, or any other file you are changing, and so that you can rollback if it doesnt work.

Good luck!

Yes I am using this as my primary display and no, the other OSes work fine. The error is displayed at bootup. Thanks for the suggestion and I will give it a shot.

---

### Post by santellan17585 on 2009-07-12
Okay, so I tried that and still no dice. Weirdest part of this whole thing is that xorg.conf is actually blank. The file contains nothing at all. I could be doing something wrong, but when trying to edit the file, there is nothing there.

---

### Post by santellan17585 on 2009-07-12
I got Ubuntu to boot without prompting for a million different things now by copying someones xorg.conf. Here is what it says:

Section "Module"
    Load "dbe" # Double-Buffering Extension
    Load "v4l" # Video for Linux
    Load "extmod"
    Load "type1"
    Load "freetype"
    Load "glx" # 3D layer
    Load "dri" # direct rendering
EndSection

Section "InputDevice"
    Identifier "Keyboard1"
    Driver "kbd"
    Option "XkbModel" "pc105"
    Option "XkbLayout" "us"
    Option "XkbOptions" "compose:rwin"
EndSection

Section "InputDevice"
    Identifier "Mouse1"
    Driver "mouse"
    Option "Protocol" "ExplorerPS/2"
    Option "Device" "/dev/mouse"
EndSection

Section "Monitor"
    Identifier "monitor1"
    VendorName "Generic"
    ModelName "Flat Panel 1360x768"
    HorizSync 31.5-48.0
    VertRefresh 56.0-65.0

    # Monitor preferred modeline (60.0 Hz vsync, 64.0 kHz hsync, ratio 5/4)
    ModeLine "1280x1024" 108 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync

    # TV fullscreen mode or DVD fullscreen output.
    # 768x576 @ 79 Hz, 50 kHz hsync
    ModeLine "768x576"     50.00  768  832  846 1000   576  590  595  630

    # 768x576 @ 100 Hz, 61.6 kHz hsync
    ModeLine "768x576"     63.07  768  800  960 1024   576  578  590  616

    # modeline generated by gtf(1) [handled by XFdrake]
    ModeLine "1360x768_120"  183.30  1360 1456 1608 1856  768 769 772 823  -HSync +Vsync

    # modeline generated by gtf(1) [handled by XFdrake]
    ModeLine "1360x768_100"  149.78  1360 1456 1600 1840  768 769 772 814  -HSync +Vsync

    # modeline generated by gtf(1) [handled by XFdrake]
    ModeLine "1360x768_85"  125.12  1360 1448 1592 1824  768 769 772 807  -HSync +Vsync

    # modeline generated by gtf(1) [handled by XFdrake]
    ModeLine "1360x768_75"  108.75  1360 1440 1584 1808  768 769 772 802  -HSync +Vsync

    # modeline generated by gtf(1) [handled by XFdrake]
    ModeLine "1360x768_60"  84.72  1360 1424 1568 1776  768 769 772 795  -HSync +Vsync

    # modeline generated by gtf(1) [handled by XFdrake]
    ModeLine "1360x768_50"  69.61  1360 1416 1560 1760  768 769 772 791  -HSync +Vsync
EndSection

Section "Device"
    Identifier "device1"
    Driver "vesa"
    Option "DPMS"
EndSection

Section "Screen"
    Identifier "screen1"
    Device "device1"
    Monitor "monitor1"
    DefaultColorDepth 16

    Subsection "Display"
        Depth 24
        Modes "1360x768"
    EndSubsection
EndSection

Section "ServerLayout"
    Identifier "layout1"
    InputDevice "Keyboard1" "CoreKeyboard"
    InputDevice "Mouse1" "CorePointer"
    Screen "screen1"
EndSection

Still, I don't have the correct resolution and it does not detect my screen properly. My monitor is currently listed as "Unknown", my resolution is set to 1024x768, the refresh rate says 0Hz, and clicking "Detect Monitors" has no effect. Any ideas?

---

### Post by agathian on 2009-07-14
I recall reading somewhere about the absence of xorg.conf file in Jaunty - sorry, dont remember the details.

Good that you were able to make progress with custom xorg.conf. It has been a while since i played around with xorg.conf - and i am not an expert in that.

My suggestion would be to look at /var/org/Xorg.log. That could tell you what worked and what didnt, that way you can further tweak the xorg.conf.

alternately you could try forcing the resoultion in your login scripts or somewhere, thru the "xrandr" command. I think you can only switch to the supported set of resolutions, defined by xorg.conf.

hope this helps..

---

