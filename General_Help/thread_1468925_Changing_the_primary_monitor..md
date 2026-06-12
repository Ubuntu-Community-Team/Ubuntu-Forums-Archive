---
title: "Changing the primary monitor."
date: 2010-05-01
forum: General Help
---

### Post by kavon89 on 2010-05-01
So I decided to switch my desktop to 10.04 Ubuntu, yet not having a checkbox option in the Monitor configuration window to set a primary monitor is baffling.

```
xrandr --output HDMI1 --primary
```

That is all it takes to switch it. I've read around and places have said to add it to some gdm startup script, yet even adding it to my rc.local has no effect on boot. Also, my Login screen has the wrong resolution and is mirroring, yet when I login the resolution and extended desktop works.

I have an Intel 4 series graphics chip and no xorg.conf (I tried generating and using one with Xorg -configure but when I peeked into the file, it was poorly generated and did nothing for me.)

---

### Post by kavon89 on 2010-05-02
Bump please?

---

### Post by kavon89 on 2010-05-03
Thanks everyone, you've all been very helpful. :roll:  I'm just gonna figure out the script thing myself and join the NotifyOSD development team to fix the non-customizable way notifications are handled in Ubuntu. The dual monitor support is really terrible.

---

### Post by gmunozy2k on 2010-05-05
Having the same issue. Primary reason I upgraded to 10.04. I will live with the rest of the bugs since this works but I do need to have my monitor to be the primary with the menu's and all and have the TV be my extended secondary one. I will continue to read as well

I have an Nvidia graphics card  and no xorg.conf

Thanks I am also not very experienced.

---

### Post by neverland888 on 2010-06-06
In "Monitor Preferences" it seems that display on the left is considered as primary. So, if you want extended setup ("Same image in all monitors" disabled), turn "Off" display on the left with "On" "Off" radio, after you apply, display on the right will become primary instead of extended. Now drag left display to right and turn it "On", and it will be extended now. 

So, basically the display you want to be primary needs to be one the left side, and this only works if you drag displays while the one you want to be extended aka secondary is turned off.

This is tested on ubuntu 10.04 x86_64 intel x4500mhd with external display attached to HDMI, works fine, and configuration is saved, and will be restored on reboot, and on disconnecting/reconnecting monitors.

---

### Post by an0dos on 2010-06-06
> **gmunozy2k said:**
> Having the same issue. Primary reason I upgraded to 10.04. I will live with the rest of the bugs since this works but I do need to have my monitor to be the primary with the menu's and all and have the TV be my extended secondary one. I will continue to read as well

I have an Nvidia graphics card  and no xorg.conf

Thanks I am also not very experienced.

Go to System-->Administration
Click on "NVIDIA Server Settings"
Click on "X Server Display Configuration"

You should see both of your screens there

Click on the "Configure" button next to "Configuration"
Select "Twinview"
Click "Apply"

Move the pictures of the two screens to the layout you want.
Click the image of your computer monitor and check the block next to "Make this the primary display for the X screen". Click on "Apply" then "Quit".

---

### Post by perceptum on 2010-06-10
What I did was ...

System => Preferences => Startup Applications
Click Add
Name: XRANDR
Command: xrandr --output VGA1 --primary


This runs xrandr when you log in and sets the VGA to the primary monitor. Works well for me, even if its a hack.

Note this assumes VGA1 = your vga card and the laptop is something else. Run xrandr by itself to get an output of what's what.

HTH

Bryan

---

### Post by cacycleworks on 2010-06-20
This is awesome. I spent about an hour trying to figure out why my menus are on the wrong screen. Then was stunned to not have an xorg.conf... :P Finding out about xrandr is awesome. 

Let's add some google-able keywords so maybe others will find this:
Dual head gnome menu on wrong monitor.
New windows start on wrong monitor with dual monitors.

I have added xrandr to my startup applications and while I haven't tested it, I'm sure it will work... I've put goofy scripts in there before. :)


Thanks,
Chris

---

### Post by Bif Powell on 2010-08-08
Continue to have this problem - for a decade or more really, but for today, I would settle to just have the nvidia-setting launch properly - at this point it's telling me:

You do not appear to be using the NVIDIA X driver.  Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server.

I do that, but nothing changes.

I also find it hard to believe that I would use the xrandr, at least as shown in this thread, because both my outputs are dvi...am I wrong there?

Any guidance appreciated.

---

### Post by venturax on 2010-08-23
> **perceptum said:**
> What I did was ...
Command: xrandr --output VGA1 --primary

Thanks!!\\:D/I have struggled with this since 8.04 and now finally its over

Gotta love the forum

---

### Post by roadrunn on 2010-08-28
Hey! I've just had the same problem. And I just switched the cables :) You know, manually unplugged them and then plugged again, but in each others ports :o Simple solutions are the best solutions :D

---

### Post by Moustaffa on 2010-08-29
Hey guys,

For those of you who can't handle the terminal well, you can always use grandr instead of xrandr.

Grandr (I suppose you can install it with apt-get install grandr) gives a graphical user interface. This allowed me to see which one of my screens is VGA1 and which one is LSDV1, by looking at the maximum resolution both can have.

Turns out VGA1 is my external monitor (secondary) and LSDV1 is the laptop screen. That's why xrandr --output LSDV1 --primary didn't do anything. Check whatever the external monitor is and put that in the command.

Greets

PS: I'm aware you can do this easily with xrandr, because the external screen is either one of the 2 that are connected, but I learned not to mess with the terminal if unsure; that's where grandr helped me.

---

### Post by venturax on 2010-08-30
> **roadrunn said:**
> Hey! I've just had the same problem. And I just switched the cables :) You know, manually unplugged them and then plugged again, but in each others ports :o Simple solutions are the best solutions :D

Its a bit difficult for me, as one monitor is the laptopscreen ;-)

---

### Post by Zambini on 2010-11-17
> **kavon89 said:**
> ```
xrandr --output HDMI1 --primary
```

I've been searching for hours on this. This should be stickied :D

For people who don't like terminals:

```
xrandr -q
``` will list your currently plugged in monitors, giving you the name you should use when setting primary.

:D

---

### Post by GiveLove on 2010-11-22
Thank you Perceptum!!! You sir deserve a GOLD star!!! :D :D :D 

Here's my situation. I'm running LinuxMint 10 (Based on Ubuntu 10.10), with an AMD 5770 graphics card (2 x DVI ports, 1 HDMI, and 1 DP), using the proprietary AMD drivers installed by the additional drivers software tool, an Asus VW226H connected via DVI as my primary display, and a Hannspree ST42DMSB 1080p HDTV connected via a HDMI cable as my secondary display, in "Multi-display desktop" mode in AMD CCC. (Used for full screen video watching) 

I tried swapping the DVI ports used for the Asus monitor, as some suggested, and also tried the aticonfig commands to no use. (Reference the following link for aticonfig info)
[http://ubuntuforums.org/showthread.php?t=1609704](http://ubuntuforums.org/showthread.php?t=1609704)

But it it Perceptums post# 7 that did the trick. There is a little more involved though that I'd like to add to help other users. 

You have to find out what the name of the monitor is by doing a query in Terminal.

```
xrandr -q
```

Scroll through the output. If your monitors are different resolutions, that's how you will tell which is which. And it's possible that the name may also help identify it. The name appears to always be a four digit alpha-numeric identifier. My primary Asus monitor was named DFP3, and the HDTV DFP2. (I'd guess it stands for Digital Flat Panel) So how I could tell them apart was the difference in resolutions showing in the output. Asus is 1920 X 1200, and the HDTV 1920 X 1080. 

You can test whether this solution works for you first by entering it in Terminal. 

So my command was:

```
xrandr --output DFP3 --primary
```

Yours may differ depending on the name being used by xrandr for your primary monitor. Once you've verified that it works. Follow Perceptum's instructions in post# 7. And it's also a good idea to add a brief descriptive sentence in the comments area when adding this new entry into the startup applications preferences, so you will be reminded of what it is for in the future. Good luck and thanks again! :D

GiveLove

---

### Post by tamashumi on 2011-10-15
Hi guys,

For me worked adding one line to xorg.conf under monitor section's I want to be primary:
```

Section "Monitor"
...
    Option "Primary" "true"
EndSection

```

I'm on Natty 11.04 with ATI HD 9650 Catalyst 11.9 driver.

This card has 5 ports and I was switching monitors between them in many different ways. Nothing helped. Nor helped xrandr.

Strange thing is that couple of hours ago with my previous GPU HD 4870 and Catalyst 11.8 it was working without the line added (the same xorg.cong - well almost the same as video port numbers changed but I adjusted them to be correct).

Don't ask me where I get this info. It was out from top of my head as an act of desperation. Like "I will write this here and... w00t!? it works!"

Hope it will help someone :)

---

### Post by guikubivan on 2013-02-08
> **tamashumi said:**
> Hi guys,

For me worked adding one line to xorg.conf under monitor section's I want to be primary:
[code]
Section "Monitor"
...
    Option "Primary" "true"
EndSection


This worked for me, but now, my primary's monitor resolution is decreased to the secondary's. :(

---

### Post by wildmanne39 on 2013-02-08
If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---

