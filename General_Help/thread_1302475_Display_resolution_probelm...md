---
title: "Display resolution probelm.."
date: 2009-10-27
forum: General Help
---

### Post by rahilm on 2009-10-27
Ok this is a very old problem, something i didn't care about solving until now.
Back when i was new to ubuntu ..which was 8.04.. i had set my display resolution as 1280x1024.
Then I installed 8.10 (clean) and set the resolution to 1280x1024
But suddenly, for no reasons that i could recall the resolution went back to 640x480.
I went to display preferences to change it back to 1280x1024 but was surprised to see that the option wasn't available!!
I can go as far as 1152x864 (4:3) and 1360x768 (16:9).
I ignored it as 1152 was enough then
I thought I may have accidentally edited some configuration file
Then I installed 9.04 (after formatting the drive and doing a clean install).
But surprisingly, 1280x1024 is still not available.
I don't get it.
Nothing has changed since 8.04, no hardware changes , no replacements. Still ubuntu now fails to recognize that my monitor can display 1280x768.

I don't have any ATI or NVIDIA card installed , all there is, is the on board intel card (128mb i gues... i don't know how to check it)

Windows XP that i had all along can go beyond 1280x1024. I tried puppy linux. Even puppy could go to 1280x1024

What's wrong with Ubuntu, and how can i fix it???

---

### Post by grizato on 2009-10-27
I don't know if this is the same problem but a while back I had Kubuntu and it had the same problem so I unplugged the power cable for a minute and put it back in again and it seemed to work.

Another fix would be to go onto the ubuntu fixig thing at startup(press ESC to eneter the menu.. 5,4...), I vaguely remember there being an option somewher to 'fix graphics poblems', I hope this helps!:D

---
grizato
[www.tecky-junk.blogspot.com](www.tecky-junk.blogspot.com)

---

### Post by rahilm on 2009-10-27
No it doesn't help

---

### Post by Anonymousable on 2009-10-27
What is your graphics card, and which drivers are you using? The drivers are the most common source of problems like this.

---

### Post by dylan_newb on 2009-10-27
try looking at this 
[https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)

---

### Post by rahilm on 2009-10-27
> **Anonymousable said:**
> What is your graphics card, and which drivers are you using? The drivers are the most common source of problems like this.

I don't know. As is said my PC doesn't have NVIDIA for sure. no ATI.. It is on borad intel.. I don't know how to check it ( in windows i do 'dxdiag')

I installed nothing nothing related to my graphic driver . Everything works out of the box (Even compiz-fusion effects works perfectly) except the resolution issue.

But how come 8.04 was able to get 1280x1024 but 8.10 and 9.04 can't.

---

### Post by carml on 2009-10-27
Enter this command in your terminal to know what your graphic card is ```
 lspci | grep VGA 
```
:)

---

### Post by rahilm on 2009-10-27
> **carml said:**
> Enter this command in your terminal to know what your graphic card is ```
 lspci | grep VGA 
```:)

Here's the output
00:02.0 VGA compatible controller: Intel Corporation 82946GZ/GL Integrated Graphics Controller (rev 02)

---

### Post by rahilm on 2009-10-29
...

---

### Post by akakingess on 2009-10-29
I could have sworn that in the last 2 releases or so, that there has been an issue with Intel graphics, some have said that it used to work and hasn't since then, but supposedly, 9.10 which is of course being released TODAY that this issue has been addressed and hopefully fixed. I think if you do a thorough search on the forums that date back quite a bit, you will find a lot of unhappy people about the Intel graphics support being lost for the last 2 or 3 releases. This is just stuff that I have read and can't remember where (probably here somewhere), but as I don't have an Intel graphics card or chipset I couldn't tell you the fix or exact problem.  I know this hasn't helped much, but I do believe that if you can get a LiveCD for 9.10 sometime today you may be happily surprised to see the problem resolved. Good Luck.

---

### Post by dandnsmith on 2009-10-29
I wonder if [this posting](http://roland-lopez.blogspot.com/2007/03/auto915resolution-ubuntu-resolution-fix.html) might contain a solution to the problem

---

### Post by rahilm on 2009-11-15
Well...to be honest i completely forgot that i had posted this question over here..but then today , i got the 9.10 Live CD.
I came back to post this and I saw this message.

> **akakingess said:**
> I could have sworn that in the last 2 releases or so, that there has been an issue with Intel graphics, some have said that it used to work and hasn't since then, but supposedly, 9.10 which is of course being released TODAY that this issue has been addressed and hopefully fixed. I think if you do a thorough search on the forums that date back quite a bit, you will find a lot of unhappy people about the Intel graphics support being lost for the last 2 or 3 releases. This is just stuff that I have read and can't remember where (probably here somewhere), but as I don't have an Intel graphics card or chipset I couldn't tell you the fix or exact problem. I know this hasn't helped much, but I do believe that if you can get a LiveCD for 9.10 sometime today you may be happily surprised to see the problem resolved. Good Luck.



What happened in my case:
Ubuntu 9.10 loaded in 800x600 resolution.
So i opened Display Preferences to change it, but
it has only 600x400 and 800x600 in the options.

So for those who say Ubuntu 9.10 has improved support for intel graphics, in my case it has gotten worse.

Forget about 1280x1024 ..i can't even get 1024x768



That's too bad...I'll try to find a solution but honestly this is one issue that should be out of the box. I mean, i never had ANY problems with XP, 8.04. a little with 8.10,9.04 but this is far severe. And i don't think anybody likes to browse for solutions without a good resolution

---

### Post by rahilm on 2009-11-15
bump...

---

### Post by ctult on 2009-11-15
I had the same problem. :(

---

### Post by rahilm on 2009-11-16
My 9.10 Live-CD does not contain the /etc/X11/xorg.conf file..
Is this normal??

---

### Post by rahilm on 2009-11-16
bump...

---

### Post by realzippy on 2009-11-16
> **rahilm said:**
> My 9.10 Live-CD does not contain the /etc/X11/xorg.conf file..
Is this normal??

Yes.Things have chanched in karmic....

---

### Post by P4man on 2009-11-16
Yes its normal that you dont have a xorg.conf.

You can make one however. Before doing that, can you open a terminal and type

```
xrandr
```

and copy paste the output here?

---

### Post by rahilm on 2009-11-16
This is the output of xrandr from my currently installed ubuntu 9.04

Screen 0: minimum 320 x 200, current 1152 x 864, maximum 1360 x 1360
VGA connected 1152x864+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1360x768       59.8  
   1152x864       60.0* 
   1024x768       60.0  
   800x600        60.3  
   640x480        59.9  



I'll post the output from the 9.10 Live-CD in a moment

---

### Post by rahilm on 2009-11-16
Here is the output of xrandr form my Ubuntu 9.10 Live-CD

Screen 0: minimum 320 x 200, current 800 x 600, maximum 8192 x 8192
VGA1 connected 800x600+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   800x600        60.3* 
   640x480        59.9

---

### Post by P4man on 2009-11-16
Try this in a terminal:

```
xrandr --newmode "1024x768_60.00"   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync
xrandr --addmode VGA1 1024x768_60.00
xrandr --output VGA1 --mode 1024x768_60.00
```

If you want other resolutions, do the same by generating the "newmode" modeline with cvt:

```
cvt x-res y-res refresh
```

For instance:

```
*cvt 1360 768 60*
# 1360x768 59.80 Hz (CVT) hsync: 47.72 kHz; pclk: 84.75 MHz
Modeline **"1360x768_60.00"   84.75  1360 1432 1568 1776  768 771 781 798 -hsync +vsync**
```


then copy paste the bold part to create the new mode (the name is in green):

```
xrandr --newmode **"[COLOR="Green"]1360x768_60.00[/COLOR]"   84.75  1360 1432 1568 1776  768 771 781 798 -hsync +vsync**
```

then link it to your VGA1 output:

```
xrandr --addmode VGA1 [COLOR="Green"]1360x768_60.00[/COLOR]
```
And switch to it:
```
xrandr --output VGA1 --mode [COLOR="Green"]1360x768_60.00[/COLOR]
```

This is not persistent but if it works we can add the stuff to your xorg.conf to make it persistent.

---

### Post by rahilm on 2009-11-16
> **P4man said:**
> Try this in a terminal:

```
xrandr --newmode "1024x768_60.00"   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync
xrandr --addmode VGA1 1024x768_60.00
xrandr --output VGA1 --mode 1024x768_60.00
```If you want other resolutions, do the same by generating the "newmode" modeline with cvt:

```
cvt x-res y-res refresh
```For instance:

```
*cvt 1360 768 60*
# 1360x768 59.80 Hz (CVT) hsync: 47.72 kHz; pclk: 84.75 MHz
Modeline **"1360x768_60.00"   84.75  1360 1432 1568 1776  768 771 781 798 -hsync +vsync**
```
then copy paste the bold part to create the new mode (the name is in green):

```
xrandr --newmode **"[COLOR=Green]1360x768_60.00[/COLOR]"   84.75  1360 1432 1568 1776  768 771 781 798 -hsync +vsync**
```then link it to your VGA1 output:

```
xrandr --addmode VGA1 [COLOR=Green]1360x768_60.00[/COLOR]
```And switch to it:
```
xrandr --output VGA1 --mode [COLOR=Green]1360x768_60.00[/COLOR]
```This is not persistent but if it works we can add the stuff to your xorg.conf to make it persistent.


It works!!!
Thanks...
How do I make it persistent?

---

### Post by P4man on 2009-11-16
> **rahilm said:**
> It works!!!
Thanks...
How do I make it persistent?

Im not entirely sure as I have no experience with intel gpu's.
Would be easiest if you could start with a base xorg.conf. If you run 

```
sudo dpkg-reconfigure xserver-xorg
```

Does it generate a (mostly empty) xorg.conf ? If so please post it (/etc/X11/xorg.conf)

---

### Post by rahilm on 2009-11-16
Here is xorg.conf

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
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection

```

---

### Post by jssudheer on 2009-11-16
> **P4man said:**
> Try this in a terminal:

```
xrandr --newmode "1024x768_60.00"   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync
xrandr --addmode VGA1 1024x768_60.00
xrandr --output VGA1 --mode 1024x768_60.00
```If you want other resolutions, do the same by generating the "newmode" modeline with cvt:

```
cvt x-res y-res refresh
```For instance:

```
*cvt 1360 768 60*
# 1360x768 59.80 Hz (CVT) hsync: 47.72 kHz; pclk: 84.75 MHz
Modeline **"1360x768_60.00"   84.75  1360 1432 1568 1776  768 771 781 798 -hsync +vsync**
```then copy paste the bold part to create the new mode (the name is in green):

```
xrandr --newmode **"[COLOR=Green]1360x768_60.00[/COLOR]"   84.75  1360 1432 1568 1776  768 771 781 798 -hsync +vsync**
```then link it to your VGA1 output:

```
xrandr --addmode VGA1 [COLOR=Green]1360x768_60.00[/COLOR]
```And switch to it:
```
xrandr --output VGA1 --mode [COLOR=Green]1360x768_60.00[/COLOR]
```This is not persistent but if it works we can add the stuff to your xorg.conf to make it persistent.


Thank you it solved my problem

---

### Post by P4man on 2009-11-16
Try this for 1360x768 @60Hz:

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
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
[COLOR="DarkRed"]    Modeline "1360x768_60.00"   84.75  1360 1432 1568 1776  768 771 781 798 -hsync +vsync[/COLOR]
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection

```

You'll have to restart X after that

---

### Post by rahilm on 2009-11-16
Nice

---

### Post by rahilm on 2009-11-16
Working in 9.04, now i am going to check for the 9.10 live-cd..
hopefully, it'll work..
But Karmic doesn't have an xorg.conf file.
then what?

---

### Post by P4man on 2009-11-16
> **rahilm said:**
> Working in 9.04, now i am going to check for the 9.10 live-cd..
hopefully, it'll work..
But Karmic doesn't have an xorg.conf file.
then what?

Create one. Just copy paste the above one, it should work just as well. But if you dont mind, do let me know if 
sudo dpkg-reconfigure xserver-xorg
creates a default xorg.conf file or not.

---

### Post by rahilm on 2009-11-16
> **P4man said:**
> Create one. Just copy paste the above one, it should work just as well. But if you dont  mind, do let me know if 
sudo dpkg-reconfigure xserver-xorg
creates a default xorg.conf file or not.

sudo dpkg-reconfigure xserver-xorg
does nothing, but i copied my xorg.conf file over to ubuntu 9.10 and it is working fine

---

### Post by GSX550ES on 2009-11-20
I'm afraid I'm still having problems & this seems the best post rather than starting a new one. I did xrandr & got the following output
Screen 0: minimum 400 x 300, current 1360 x 768, maximum 1360 x 864
default connected 1360x768+0+0 0mm x 0mm
   1360x768       60.0* 
   1152x864       60.0  
   1024x768       75.0     70.0     60.0  
   832x624        75.0  
   800x600        75.0     72.0     60.0     56.0     65.0  
   840x525        70.0     60.0  
   700x525        75.0     70.0     60.0  
   640x512        75.0     60.0  
   720x450        60.0  
   640x480        75.0     73.0     67.0     60.0  
   720x400        70.0  
   680x384        60.0  
   576x432        75.0     70.0     60.0  
   512x384        75.0     70.0     60.0  
   416x312        75.0  
   400x300        75.0     72.0     60.0     56.0  
   1360x864       60.0 

But a couple of things here I don't have a VGA1 output to do the addoutput command also my monitor supports higher resolution than these up to 1680x1050. I also tried the cvt command & adding it to a xorg.conf file but when I did that it wouldn't boot & had to reboot to recovery & delete the file.

Output of lspci

00:00.0 RAM memory: nVidia Corporation MCP55 Memory Controller (rev a2)
00:01.0 ISA bridge: nVidia Corporation MCP55 LPC Bridge (rev a3)
00:01.1 SMBus: nVidia Corporation MCP55 SMBus (rev a3)
00:02.0 USB Controller: nVidia Corporation MCP55 USB Controller (rev a1)
00:02.1 USB Controller: nVidia Corporation MCP55 USB Controller (rev a2)
00:05.0 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a3)
00:05.1 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a3)
00:05.2 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a3)
00:06.0 PCI bridge: nVidia Corporation MCP55 PCI bridge (rev a2)
00:0a.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a3)
00:0b.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a3)
00:0c.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a3)
00:0d.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a3)
00:0e.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a3)
00:0f.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
**10:00.0 VGA compatible controller: Matrox Graphics, Inc. MGA G200e [Pilot] ServerEngines (SEP1) (rev 02)**
11:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5722 Gigabit Ethernet PCI Express

Hope somebody can help.

Alan...

---

### Post by P4man on 2009-11-20
What modeline did you try to add? Did you generate it with (edit) cvt and ajusted the resolution and refresh rate to match your monitor?

Also this seems like an embedded VGA from a server board. Are you sure the onboard videocard is actually capable of higher resolutions?

---

### Post by realzippy on 2009-11-20
How to run the xrandr --addmode command in this case?

xrandr -q:

Screen 0: minimum 400 x 300, current 1360 x 768, maximum 1360 x 864
[COLOR="Red"]default[/COLOR] connected 1360x768+0+0 0mm x 0mm

no VGA1,VGA-1,LVDS,DVI ?
*default* does not work ;-)

---

### Post by GSX550ES on 2009-11-20
> **P4man said:**
> What modeline did you try to add? Did you generate it with (edit) cvt and ajusted the resolution and refresh rate to match your monitor?

Also this seems like an embedded VGA from a server board. Are you sure the onboard videocard is actually capable of higher resolutions?

I tried to add a modeline in xorg.conf 1680 1050 65.29 59.954 which is what Samsung have on their website.

It is an embedded VGA on a Proliant ML115 G5 I don't know what resolutions it can handle as there is nothing in the specifications, in the specs it says it should have a nvidia graphics but as you can see from the line above it has a Matrox.

Ihave just done another clean install & still have the same issues.

Alan...

---

### Post by P4man on 2009-11-21
That is not a proper mode line for xorg.
try this in a terminal
```

xrandr --newmode  "1680x1050_60.00"  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync
```

Copy paste the output of ```
xrandr
``` again.
Then try this:
```

xrandr  --mode 1680x1050_60.00
```

---

### Post by GSX550ES on 2009-11-21
> alan@box:~$ xrandr --newmode  "1680x1050_60.00"  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync
alan@box:~$ xrandr
Screen 0: minimum 400 x 300, current 1360 x 768, maximum 1360 x 864
default connected 1360x768+0+0 0mm x 0mm
   1360x768       60.0* 
   1152x864       60.0  
   1024x768       75.0     70.0     60.0  
   832x624        75.0  
   800x600        75.0     72.0     60.0     56.0     65.0  
   840x525        70.0     60.0  
   700x525        75.0     70.0     60.0  
   640x512        75.0     60.0  
   720x450        60.0  
   640x480        75.0     73.0     67.0     60.0  
   720x400        70.0  
   680x384        60.0  
   576x432        75.0     70.0     60.0  
   512x384        75.0     70.0     60.0  
   416x312        75.0  
   400x300        75.0     72.0     60.0     56.0  
   1360x864       60.0  
  1680x1050_60.00 (0x13c)  146.2MHz
        h: width  1680 start 1784 end 1960 total 2240 skew    0 clock   65.3KHz
        v: height 1050 start 1053 end 1059 total 1089           clock   60.0Hz


alan@box:~$ xrandr  --mode 1680x1050_60.00
usage: xrandr [options]
  where options are:
  -display <display> or -d <display>
  -help
  -o <normal,inverted,left,right,0,1,2,3>
            or --orientation <normal,inverted,left,right,0,1,2,3>
  -q        or --query
  -s <size>/<width>x<height> or --size <size>/<width>x<height>
  -r <rate> or --rate <rate> or --refresh <rate>
  -v        or --version
  -x        (reflect in x)
  -y        (reflect in y)
  --screen <screen>
  --verbose
  --dryrun
  --nograb
  --prop or --properties
  --fb <width>x<height>
  --fbmm <width>x<height>
  --dpi <dpi>/<output>
  --output <output>
      --auto
      --mode <mode>
      --preferred
      --pos <x>x<y>
      --rate <rate> or --refresh <rate>
      --reflect normal,x,y,xy
      --rotate normal,inverted,left,right
      --left-of <output>
      --right-of <output>
      --above <output>
      --below <output>
      --same-as <output>
      --set <property> <value>
      --scale <x>x<y>
      --transform <a>,<b>,<c>,<d>,<e>,<f>,<g>,<h>,<i>
      --off
      --crtc <crtc>
      --panning <w>x<h>[+<x>+<y>[/<track:w>x<h>+<x>+<y>[/<border:l>/<t>/<r>/<b>]]]
      --gamma <r>:<g>:<b>
      --primary
  --noprimary
  --newmode <name> <clock MHz>
            <hdisp> <hsync-start> <hsync-end> <htotal>
            <vdisp> <vsync-start> <vsync-end> <vtotal>
            [+HSync] [-HSync] [+VSync] [-VSync]
  --rmmode <name>
  --addmode <output> <name>
  --delmode <output> <name>

These are the outputs of the commands.

Alan...

---

### Post by P4man on 2009-11-21
Ok. Seems you still have to add the mode.
Try this:

create the mode again if you rebooted meanwhile:
```

xrandr --newmode  "1680x1050_60.00"  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync
```

Then add the mode:

```
xrandr --addmode default 1680x1050_60.00
```

then switch to it:

```

xrandr --output default --mode 1680x1050_60.00
```

If that last line fails you can also check system > preferences > display as the new resolution should be in there.

---

### Post by supernova42 on 2009-11-21
what would be a code like that for the res 1280x1024 at 60Hz

---

### Post by P4man on 2009-11-21
> **supernova42 said:**
> what would be a code like that for the res 1280x1024 at 60Hz

open a terminal and type

```
cvt x-res y-res refresh
```

it will spit out the modeline for use in xorg or with xrandr

---

### Post by goldsniper on 2009-11-21
what? no gui?:popcorn:

---

### Post by GSX550ES on 2009-11-21
> 
alan@box:~$ xrandr --newmode  "1680x1050_60.00"  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync
alan@box:~$ xrandr --addmode default 1680x1050_60.00
alan@box:~$ xrandr --output default --mode 1680x1050_60.00
xrandr: screen cannot be larger than 1360x864 (desired size 1680x1050)
alan@box:~$

Thanks for the reply, this is the result of the commands.

Alan...

---

### Post by P4man on 2009-11-21
Then it looks as if your videocard is unable to handle that resolution. Nothing can be done Im afraid , other than plugging in a different videocard.

---

### Post by GSX550ES on 2009-11-21
Yeah seems that way, is there a command that you can probe the card to find it's highest resolution? Think I'll end up making this headless to use for samba & torrents, then yet myself a new PC  for my desktop.

Cheers

Alan...

---

### Post by P4man on 2009-11-21
Dont know any other way than what you just did. Perhaps though you can assign more videoram in the bios and that will allow higher res? Perhaps it only has like 2 or 4Mb now?

---

### Post by GSX550ES on 2009-11-21
Thanks for all your help, I have just found this in Xorg.0.log after reading another post

(II) MGA(0): Not using driver mode "1680x1050" (width too large for virtual size)
(II) MGA(0): Not using driver mode "1280x1024" (mode requires too much memory bandwidth)
(II) MGA(0): Not using driver mode "1280x960" (mode requires too much memory bandwidth)
(II) MGA(0): Not using driver mode "1152x864" (mode requires too much memory bandwidth)

The prolem appears to be the onboard card.

Alan...

---

### Post by realzippy on 2009-11-22
> **GSX550ES said:**
> Thanks for all your help, I have just found this in Xorg.0.log after reading another post

(II) MGA(0): Not using driver mode "1680x1050" (width too large for virtual size)
(II) MGA(0): Not using driver mode "1280x1024" (mode requires too much memory bandwidth)
(II) MGA(0): Not using driver mode "1280x960" (mode requires too much memory bandwidth)
(II) MGA(0): Not using driver mode "1152x864" (mode requires too much memory bandwidth)

The prolem appears to be the onboard card.

Alan...



(II) MGA(0): Not using driver mode "1680x1050" ([COLOR="Red"]width too large for virtual size[/COLOR])

I think virtual size is set in xorg.conf (of course depending on video RAM)...can you post your /etc/X11/xorg.conf file please?

---

### Post by GSX550ES on 2009-11-22
> **realzippy said:**
> can you post your /etc/X11/xorg.conf file please?

Actually admitted defeat on this & went out & bought a nVidia card & put it in a slot. Once booted I can now get 1650x1050 & it even recognises my monitor as the Samsung it is. Just looked & I don;t have a xorg.conf file.

Next thing is to work out how to use 2 monitors.

Alan...

---

### Post by aliozer on 2009-12-09
I am having the same problem but I don't think that my card cannot handle the high resolution. My on-board nvdia card and Samsung monitor combination worked fine with 1650X1080 resolution before when I had Ubuntu 8.10. Now I upgraded to 9.10 and I cannot get the resolution higher than 1024x768. I tried both editing the xorg.conf file and the xrandr commands, with and without the nvdia driver, and no luck. With xrandr, I sometimes get "xrandr: Configure crtc 0 failed" error and sometimes "screen cannot be larger than ..." error after the last step (xrandr --output default --mode ...). Any ideas?

---

### Post by aliozer on 2009-12-09
Here is my /etc/X11/xorg.conf file. Refresh rates are for Samsung Syncmaster T200

```

# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder58)  Fri Aug 14 18:33:37 PDT 2009

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Unknown"
    HorizSync       30.0 - 81.0
    VertRefresh     56.0 - 75.0
    #Option         "DPMS"
    Modeline "1680x1050_50"  119.50  1680 1776 1944 2208  1050 1053 1059 1083 -hsync +vsync
    Option "PreferredMode" "1680x1050_50"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
	Modes "1680x1050_50"
	#Virtual 1680 1050
    EndSubSection
EndSection

```

---

### Post by aliozer on 2009-12-09
And here is the output of xrandr commands:
```

$cvt 1680 1050 50
# 1680x1050 49.97 Hz (CVT 1.76MA) hsync: 54.12 kHz; pclk: 119.50 MHz
Modeline "1680x1050_50.00"  119.50  1680 1776 1944 2208  1050 1053 1059 1083 -hsync +vsync

$ xrandr
Screen 0: minimum 320 x 240, current 1024 x 768, maximum 1024 x 768
default connected 1024x768+0+0 0mm x 0mm
   1024x768       50.0*    51.0     52.0  
   960x600        53.0  
   960x540        54.0  
   840x525        55.0     56.0     57.0  
   832x624        58.0  
   800x600        59.0     60.0     61.0     62.0     63.0     64.0  
   800x512        65.0  
   720x450        66.0  
   680x384        67.0     68.0  
   640x512        69.0     70.0  
   640x480        71.0     72.0     73.0     74.0     75.0     76.0  
   576x432        77.0     78.0     79.0     80.0  
   512x384        81.0     82.0     83.0  
   416x312        84.0  
   400x300        85.0     86.0     87.0     88.0  
   320x240        89.0     90.0     91.0  

$ xrandr --newmode "1680x1050_50.00"  119.50  1680 1776 1944 2208  1050 1053 1059 1083 -hsync +vsync

$ xrandr
Screen 0: minimum 320 x 240, current 1024 x 768, maximum 1024 x 768
default connected 1024x768+0+0 0mm x 0mm
   1024x768       50.0*    51.0     52.0  
   960x600        53.0  
   960x540        54.0  
   840x525        55.0     56.0     57.0  
   832x624        58.0  
   800x600        59.0     60.0     61.0     62.0     63.0     64.0  
   800x512        65.0  
   720x450        66.0  
   680x384        67.0     68.0  
   640x512        69.0     70.0  
   640x480        71.0     72.0     73.0     74.0     75.0     76.0  
   576x432        77.0     78.0     79.0     80.0  
   512x384        81.0     82.0     83.0  
   416x312        84.0  
   400x300        85.0     86.0     87.0     88.0  
   320x240        89.0     90.0     91.0  
  1680x1050_50.00 (0x1ea)  119.5MHz
        h: width  1680 start 1776 end 1944 total 2208 skew    0 clock   54.1KHz
        v: height 1050 start 1053 end 1059 total 1083           clock   50.0Hz

$ xrandr --addmode default "1680x1050_50.00"

$ xrandr --output default --mode "1680x1050_50.00"
xrandr: screen cannot be larger than 1024x768 (desired size 1680x1050)



```

---

### Post by aliozer on 2009-12-09
Just a final word, I also tried above with 60Hz refresh rate, which is the optimal refresh rate in the manual but the results were the same. It just will not go above 1024x768. Any ideas?

---

### Post by Cclips on 2010-01-17
I'm also having this issue, I got as far as to have the resolution listed in the display settings, but when I tried to set it I get a pop up saying it can't be set "could not set the configuration to crtc32.1" Or something along those lines. The resolution is NOT displayed in the Nvidia control settings at all, and I know the card supports this resolution.

Edit: So I've gotten it to display and recognize the proper resolution by following this guide and using nvidia-settings.

[http://turbulentsky.com/ubuntu-904-nvidia-driver-screen-resolution-problem.html]("http://turbulentsky.com/ubuntu-904-nvidia-driver-screen-resolution-problem.html")

Problem now being that the resolution resets every time X is restarted.

---

