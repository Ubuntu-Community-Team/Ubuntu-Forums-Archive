---
title: "Resolution 1440x900 Xorg help - sis 671 (acer m1610)"
date: 2010-11-27
forum: General Help
---

### Post by Gazzamit on 2010-11-27
[SIZE=2]I have an acer m1610.

Built in graphics is sis 671.

Monitor is emprex lm1905 max res 1440 x 900.

After 1st fresh install of 10.10 X does not select 1440 x 900, but instead 1280 x 1024.

I have temporarily tried another graphics card from another PC and that runs 1440 x 900 without a problem.

Output from [/SIZE]```
sudo X :2 -configure
```[SIZE=2] does not give any useful info.

From xorg.0.log I have identified a modeline which should specify the correct settings for the monitor. The modeline is identical with both graphic cards and reads as follows:

"1440x900" 136.75 1440 1536 1688 1936 900 903 909 942 -hsync +vsync

I have tried the following commands:
[/SIZE]```
xrandr --newmode "1440x900" 136.75 1440 1536 1688 1936 900 903 909 942 -hsync +vsync

xrandr --addmode default 1440x900

xrandr --output default --mode 1440x900
```[SIZE=2]

This gives error that resolution could not be set (error crtc 262).

I have tried the following Xorg.conf file, but get logged into tty1 on reboot, and gdm login screen does not display (black screen, white text). [/SIZE][SIZE=2]
Horizsync and vertrefresh taken from xorg.0.log.[/SIZE]
[SIZE=2]
[/SIZE]```
Section "Device"
        Identifier      "Configured Video Device"
        Driver          "vesa"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
        HorizSync     31.0 - 84.0
        VertRefresh     56.0 - 76.0
 
       Modeline "1440x900" 136.75 1440 1536 1688 1936 900 903 909 942 -Hsync +Vsync
       DisplaySize 1440x900
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
        SubSection "Display"
            Modes   "1440X900"
            Depth           24
        EndSubSection
[SIZE=2]
EndSection
[/SIZE]
```[SIZE=2]
[/SIZE]
[SIZE=2] Any advice would be much appreciated as I cant leave working graphics card in this machine.

Regards,

Gaz.







[/SIZE]

---

### Post by dandnsmith on 2010-11-27
You don't say what sort of connection there is to the monitor - are you by any chance using a VGA cable?

I think the problem is likely to be in the graphics driver which is being invoked. You might be able to see which one is used for each graphics card by using lsmod.

---

### Post by Vaphell on 2010-11-27
does vesa support that resolution at all? i guess it does not

install a dedicated driver for your chipset
[http://forum.nginx.org/read.php?26,102167](http://forum.nginx.org/read.php?26,102167)

---

### Post by Gazzamit on 2010-12-01
Hello,

Yes VGA connection.

I looked for the proprietary driver for my sis card and found this post.

[http://ubuntuforums.org/showthread.php?t=1548547#5](http://ubuntuforums.org/showthread.php?t=1548547#5)

This gave me a sisimedia driver for 10.10. Didn't get any joy there and could not get gdm to start.

For more drivers see:

[http://ajoliveira.com/ajoliveira/uk/software/xorg.php](http://ajoliveira.com/ajoliveira/uk/software/xorg.php) with links to 

For Jaunty 9.04 32-bit 
  For Jaunty 9.04 64-bit 

For Karmic 9.10 32-bit  to get the driver he compiled.
For Karmic 9.10 64-bit  to get the driver he compiled.

For Lucid 10.04 32-bit to get the driver he  compiled.
For Lucid 10.04 64-bit  to get a driver he compiled with the precious help of Jonas Schwabe.

For Maverick 10.10 32-bit  to get a driver he compiled, untested because of bug #543875.
For Maverick 10.10 64-bit to get a driver he compiled.
 
Unfortunately, no joy there either.

Also see,

[http://www.ubuntugeek.com/how-to-install-sis-771671-mirage-3-video-drivers-in-ubuntu-10-04-lucid.html](http://www.ubuntugeek.com/how-to-install-sis-771671-mirage-3-video-drivers-in-ubuntu-10-04-lucid.html)

With the link to the drivers from page above I got a working version, but not at 1440x900.

At 1440x900 the screen pic looked correct but was wrong aspect ratio - everything squashed in with a black line each side of the screen.

Worked with the above driver ok at 1280 by 800 (16:10). 

Hope that helps somebody else.

In the end I just gave up as two days spent trying to fix was remedied by new card as in my case its a desktop and not a lappy.

I will take out the new graphics card and do some more testing with the sis671 at some point when I got more time.

Thanks,

Gary.

---

