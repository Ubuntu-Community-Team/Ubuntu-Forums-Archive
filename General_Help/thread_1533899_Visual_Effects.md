---
title: "Visual Effects"
date: 2010-07-18
forum: General Help
---

### Post by JonnyOSullivan on 2010-07-18
Hi, I instaled Ubuntu the other week (the newest version) and liked it so much that i done a fresh install to give it more space. Everything was was working. but now, i cant change my visual effexts. i click extra, It seaches for availble drivers, and then the screen goes blank, and then im asked if i want to keep the settings. i click yes. i exit the window, i then check again. Its on none. This didnt happen on my first install... what should i do? My graphics card can obvioulbly support it, although i dont know what my graphics card is. On System < admin < hardware drivers. it shows nothing, and at the top it says No proprietary drivers are in use on this system. Please help.

---

### Post by lkjoel on 2010-07-18
> **JonnyOSullivan said:**
> Hi, I instaled Ubuntu the other week (the newest version) and liked it so much that i done a fresh install to give it more space. Everything was was working. but now, i cant change my visual effexts. i click extra, It seaches for availble drivers, and then the screen goes blank, and then im asked if i want to keep the settings. i click yes. i exit the window, i then check again. Its on none. This didnt happen on my first install... what should i do? My graphics card can obvioulbly support it, although i dont know what my graphics card is. On System < admin < hardware drivers. it shows nothing, and at the top it says No proprietary drivers are in use on this system. Please help.
Did you try rebooting your system?

---

### Post by JonnyOSullivan on 2010-07-18
> **lkjoel said:**
> Did you try rebooting your system?

Yes, more than once.

---

### Post by roger_1960 on 2010-07-18
Hi

Have you got compiz-fusion installed?  You can check in synaptics package manager

system>administration>synaptic package manager and then search for "compiz"

Its also useful to install fusion-icon for ease of use of compiz.

---

### Post by -kg- on 2010-07-18
> **lkjoel said:**
> Did you try rebooting your system?

You shouldn't have to reboot your system.  I just did it, and it all worked without rebooting or even logging out and back on.

It concerns me that you said:

> i click extra, It seaches for availble drivers, and then the screen goes blank, and then im asked if i want to keep the settings.

This tells me that your graphics card isn't capable of accelerated graphics.  Since you said:

> This didnt happen on my first install... what should i do? My graphics card can obvioulbly support it, although i dont know what my graphics card is.

It tells me that, somehow, the drivers weren't installed for one reason or another.  Please issue the following command in terminal and post the results here:

```
lspci
```

That will tell us what graphics card you're using (among other things).

---

### Post by lkjoel on 2010-07-18
> **-kg- said:**
> You shouldn't have to reboot your system.  I just did it, and it all worked without rebooting or even logging out and back on.
I know, but rebooting usually helps.

---

### Post by JonnyOSullivan on 2010-07-19
This is what happens when i enter lspci into terminal

> 00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
02:00.0 Network controller: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01)
03:00.0 Ethernet controller: Marvell Technology Group Ltd. Device 436c (rev 16)
0a:01.0 FireWire (IEEE 1394): O2 Micro, Inc. Firewire (IEEE 1394) (rev 02)
0a:01.2 SD Host controller: O2 Micro, Inc. Integrated MMC/SD Controller (rev 02)
0a:01.3 Mass storage controller: O2 Micro, Inc. Integrated MS/xD Controller (rev 01)

---

### Post by JonnyOSullivan on 2010-07-19
> **roger_1960 said:**
> Hi

Have you got compiz-fusion installed?  You can check in synaptics package manager

system>administration>synaptic package manager and then search for "compiz"

Its also useful to install fusion-icon for ease of use of compiz.
  
Yes, Compiz is installed.

---

### Post by samstreet101 on 2010-07-19
> **JonnyOSullivan said:**
> This is what happens when i enter lspci into terminal
 
Seems like you have an intergrated graphics chipset. In my experience they tend to have trouble with advanced visual effects. They've never been able to handle it on any of the rigs i've built or used. When you said it was working on the previous installation..was that the same machine?

---

### Post by JonnyOSullivan on 2010-07-19
> **samstreet101 said:**
> Seems like you have an intergrated graphics chipset. In my experience they tend to have trouble with advanced visual effects. They've never been able to handle it on any of the rigs i've built or used. When you said it was working on the previous installation..was that the same machine?
  
Yes.I installed it on the same machine, the same way, but it's not working now. Even normal options won't work.

---

### Post by samstreet101 on 2010-07-19
That has happened to me before when I installed graphics drivers. Have you installed the graphics drivers yet? Either the proprietary ones or the open source ones? Only On one of my older machines, I got visual effects working but when I installed the drivers it stopped working. Try uninstalling them

---

### Post by JonnyOSullivan on 2010-07-19
> **samstreet101 said:**
> That has happened to me before when I installed graphics drivers. Have you installed the graphics drivers yet? Either the proprietary ones or the open source ones? Only On one of my older machines, I got visual effects working but when I installed the drivers it stopped working. Try uninstalling them

No, how can i install the graphic drivers?

---

### Post by samstreet101 on 2010-07-19
> **JonnyOSullivan said:**
> No, how can i install the graphic drivers?
 
So you currently don't have graphics drivers installed?

---

### Post by JonnyOSullivan on 2010-07-19
> **samstreet101 said:**
> So you currently don't have graphics drivers installed?

I dont think so. under system < admin < hardware drivers. It says proprietary drivers are not in use on this system.  

How can i find out is graphic drivers are installed?

---

### Post by samstreet101 on 2010-07-19
Well fist on the menu that shows your proprietary drivers (called jockey) is any of them a graphics driver? I.e does the name 'nVidia' or 'ATI' appear on that list? If not go into the ubuntu software centre and search for both ATI and nVidia and in those searches, u shud get the open source drivers (the ATI one is called ATI flgrx...not sure what the nVidia one is called). If they have a tick by them then they are installed.

---

### Post by JonnyOSullivan on 2010-07-19
> **samstreet101 said:**
> Well fist on the menu that shows your proprietary drivers (called jockey) is any of them a graphics driver? I.e does the name 'nVidia' or 'ATI' appear on that list? If not go into the ubuntu software centre and search for both ATI and nVidia and in those searches, u shud get the open source drivers (the ATI one is called ATI flgrx...not sure what the nVidia one is called). If they have a tick by them then they are installed.


Sorry, this is what it looks like: 


[[IMG]http://img841.imageshack.us/img841/5948/screenshotxq.png[/IMG]]("http://img841.imageshack.us/i/screenshotxq.png/")

---

### Post by samstreet101 on 2010-07-19
Ok so now check the software centre (or synaptic, either one for now) for the open source drivers. Search both ATI and nVidia.

---

### Post by jerenept on 2010-07-19
Try updating the repositories. open System>Administration>Update Manager and click "reload" or "refresh" or something to that effect.

---

### Post by JonnyOSullivan on 2010-07-19
> **samstreet101 said:**
> Ok so now check the software centre (or synaptic, either one for now) for the open source drivers. Search both ATI and nVidia.

[[IMG]http://img3.imageshack.us/img3/4370/screenshot2pz.png[/IMG]]("http://img3.imageshack.us/my.php?image=screenshot2pz.png")




[[IMG]http://img517.imageshack.us/img517/3850/screenshot3bk.png[/IMG]]("http://img517.imageshack.us/my.php?image=screenshot3bk.png")




[[IMG]http://img838.imageshack.us/img838/6060/screenshot4u.png[/IMG]]("http://img838.imageshack.us/my.php?image=screenshot4u.png")

---

### Post by jerenept on 2010-07-19
Maybe you should install compiz-config settings manager?

you have an Intel GMA graphics chip set. ATI and NVIDIA drivers Will probably not work.

---

### Post by samstreet101 on 2010-07-19
yeh post the results, that would be helpful. also when you've done that, open a terminal and type in 'sudo gconf-editor' you might not need sudo actually in which case just type 'gconf-editor.' Someone might want to help me out here as to the exact location of it as I'm currently sat at a windows machine not my linux machine at home, but you want to look for a tick-box that lets you turn composition on and off on your desktop.

---

### Post by jerenept on 2010-07-19
You're not suppose to "sudo" gconf-editor.

---

### Post by samstreet101 on 2010-07-19
Ah found it...when you've opened gconf-editor navigate to apps - metacity - general - then there should be a box called 'compositing_manager' is it ticked or not?

---

### Post by JonnyOSullivan on 2010-07-19
> **jerenept said:**
> Maybe you should install compiz-config settings manager?
.

How can I do this?

---

### Post by JonnyOSullivan on 2010-07-19
> **samstreet101 said:**
> Ah found it...when you've opened gconf-editor navigate to apps - metacity - general - then there should be a box called 'compositing_manager' is it ticked or not?

Its not ticked. should i tick it?

[URL="http://img836.imageshack.us/i/screenshot5.png/"]
[/URL]

---

### Post by samstreet101 on 2010-07-19
Hang on do you not have compiz manager? well you'll need that to see if compositing is actually working or not. just install it from the software centre

---

### Post by samstreet101 on 2010-07-19
> **JonnyOSullivan said:**
> Its not ticked. should i tick it?
 
[URL="http://img836.imageshack.us/i/screenshot5.png/"]
[/URL]
 
Install compiz manager first, it should enable it automatically

---

### Post by JonnyOSullivan on 2010-07-19
> **samstreet101 said:**
> Install compiz manager first, it should enable it automatically

Where should i dl it from?

---

### Post by samstreet101 on 2010-07-19
Just go to the ubuntu software centre and search for compiz, it will be the 1st or 2nd or 3rd result

---

### Post by JonnyOSullivan on 2010-07-19
> **samstreet101 said:**
> Just go to the ubuntu software centre and search for compiz, it will be the 1st or 2nd or 3rd result Open GL window and compositing manager? Already installed.

---

### Post by samstreet101 on 2010-07-19
Ok go to the top panel and go system - prefernces and see if compiz manager is listed there. If it isnt, then you havent installed it

---

### Post by samstreet101 on 2010-07-19
SHould be called 'CompizConfig Settings Manager'

---

### Post by JonnyOSullivan on 2010-07-19
> **samstreet101 said:**
> Ok go to the top panel and go system - prefernces and see if compiz manager is listed there. If it isnt, then you havent installed it

No. It's not there...

---

### Post by samstreet101 on 2010-07-19
Ok so go to software centre and install it from there, like i said it should be called CompizConfig Settings Manager

---

### Post by samstreet101 on 2010-07-19
Actually in the software centre it might be listed as 'Advanced Desktop Effects Settings (ccsm)

---

### Post by JonnyOSullivan on 2010-07-19
> **samstreet101 said:**
> Ok so go to software centre and install it from there, like i said it should be called CompizConfig Settings Manager

OK, ive installed it, now what?

---

### Post by samstreet101 on 2010-07-19
Ok now go to gconf-editor again and go apps - metacity - general and see if compositing_manager is enabled. If it isnt, then go ahead and enable it.

---

### Post by JonnyOSullivan on 2010-07-19
Yes it is.

---

### Post by samstreet101 on 2010-07-19
Have you enabled the compositing_manager in gconf-editor yet? nothing will work if that isnt enabled.

---

### Post by samstreet101 on 2010-07-19
Ok so is the wobbly windows working now?

---

### Post by JonnyOSullivan on 2010-07-19
Now under system < pref< appearence < visual effects, there is a custom option. i click extra, it searches for drivers & then says, would you like to keep settings. i click yes. i close it, check it and it is on none again. im confused.....

---

### Post by JonnyOSullivan on 2010-07-19
> **samstreet101 said:**
> Ok so is the wobbly windows working now?

Nope, the only thing that has changed is i have an extra option, custom.

---

### Post by samstreet101 on 2010-07-19
If they aren't, try enabling visual effects like you did in the begining, try just turning normal on, not advanced yet

---

### Post by JonnyOSullivan on 2010-07-19
> **samstreet101 said:**
> If they aren't, try enabling visual effects like you did in the begining, try just turning normal on, not advanced yet

It just goes straight back to none again, does ubuntu have a desktop recorder, i could show you.

---

### Post by samstreet101 on 2010-07-19
Try a reboot now, i remember having to do that on one of my machines before compositon would work

---

### Post by JonnyOSullivan on 2010-07-19
> **samstreet101 said:**
> Try a reboot now, i remember having to do that on one of my machines before compositon would work

OK, one minuite.

---

### Post by JonnyOSullivan on 2010-07-19
now i have no panels.......

---

### Post by samstreet101 on 2010-07-19
hmmm, thats odd. Turn off compositing_manager and reboot n see if they come back

---

### Post by JonnyOSullivan on 2010-07-19
OK, ive rebooted again, and its still not working....

---

### Post by JonnyOSullivan on 2010-07-19
> **samstreet101 said:**
> hmmm, thats odd. Turn off compositing_manager and reboot n see if they come back

They have, but i didnt turn of compositing_manager, i just rebooted again. But visual effects still arent working... i will record it for you.

---

### Post by samstreet101 on 2010-07-19
Did you turn off compositing_manager? and if so, have you got your panels back?

---

### Post by JonnyOSullivan on 2010-07-19
If i try to record it, i get logged out. im stumped. Please help?

---

### Post by JonnyOSullivan on 2010-07-19
> **samstreet101 said:**
> Did you turn off compositing_manager? and if so, have you got your panels back?

I just rebooted, and got my panels back, but i cannot get any visual effects still. Do confirm, compositing_manager is still on. should i turn it off?

---

### Post by JonnyOSullivan on 2010-07-19
Ok this is strange. The terminal is sort of transparent now, is this what happens on extra visuals?

---

### Post by samstreet101 on 2010-07-19
Well the visual effects at this stage are beyond me im afraid. I will say though it probably is that your graphics chip can't handle them as it is an onboard set. Usually they're very basic and can't do a lot. I would recommend buying a video card. You can get an ATI HD 4500 with 1GB GDDR for as little as £45 and you could spend less than that and get a decent one. Visual effects should work fine with one of them as you can then install the drivers for it

---

### Post by samstreet101 on 2010-07-19
> **JonnyOSullivan said:**
> Ok this is strange. The terminal is sort of transparent now, is this what happens on extra visuals?
 
Ahh it might be.. when u minimize a window does it just disappear or does it glide away?

---

### Post by samstreet101 on 2010-07-19
Off to lunch, back in an hour

---

### Post by JonnyOSullivan on 2010-07-19
I wouldnt call it gliding, its a black box that gets smaller into the bottom right corner

---

### Post by JonnyOSullivan on 2010-07-19
> **samstreet101 said:**
> Off to lunch, back in an hour

ok, thanks

---

### Post by samstreet101 on 2010-07-19
Right back now..well open up compiz settings manager (system - preferences - compiz manager) and go down to the window tools section or window utilities or whatever its called nowadays. there will be an option called 'scale.' Enable it with the tick then click the icon to go into settings. There are lots of options in there on how to activate scale, choose the one with a picture of a monitor in it. On the right hand side of that one there will be an 'enable' tickbox, make sure its enabled and choose a screen edge to activate it. You should get a little window up with tabs representing the corners/edges of a screen. Choose one of them. Now move your mouse into the part of the screen u chose. Does it do anything?

---

### Post by JonnyOSullivan on 2010-07-19
[[IMG]http://img293.imageshack.us/img293/6627/screenshotdh.png[/IMG]](http://img293.imageshack.us/my.php?image=screenshotdh.png)

So I press the picture on the right of scale?

---

### Post by samstreet101 on 2010-07-19
No click the scale icon to go into the scale properties. sorry those instructions probs werent very clear. Like i said im not at my linux machine at the mo so i cant do screenshots

---

### Post by JonnyOSullivan on 2010-07-19
Ok, one second.


[[IMG]http://img836.imageshack.us/img836/4876/screenshot1b.png[/IMG]](http://img836.imageshack.us/my.php?image=screenshot1b.png)

This happens. Now what?

---

### Post by samstreet101 on 2010-07-19
There's 3 options that say 'Initiate Window Picker for All windows' you want the one with an image of a monitor next to it. To the right of that there is a button that currently says 'None' Click the button and you should get a window come up with a monitor with lots of tabs around it

---

### Post by JonnyOSullivan on 2010-07-19
> **samstreet101 said:**
> There's 3 options that say 'Initiate Window Picker for All windows' you want the one with an image of a monitor next to it. To the right of that there is a button that currently says 'None' Click the button and you should get a window come up with a monitor with lots of tabs around it

Indeed I do. :P What should i do with them?

---

### Post by samstreet101 on 2010-07-19
Choose any of them, lets say the bottom left. So click the tab in the bottom left corner. Once you;ve done that, close that window or press apple or OK if there is a button for that. Then move your mouse to the bottom left corner of your screen...does anything happen?

---

### Post by JonnyOSullivan on 2010-07-19
> **samstreet101 said:**
> Choose any of them, lets say the bottom left. So click the tab in the bottom left corner. Once you;ve done that, close that window or press apple or OK if there is a button for that. Then move your mouse to the bottom left corner of your screen...does anything happen?

No.

---

### Post by samstreet101 on 2010-07-19
Ahh looks like visuals definetely aren't enabled then. Fraid this is beyond me now. I suspect your onboard graphics chipset isn't up to the job. Try buying a video card and installing the drivers for them. SHould work wonders, not exepensive either. Decent ATI cards are available for as little as £35. But if not then do try someone else, im not all that experienced.

---

### Post by JonnyOSullivan on 2010-07-19
> **samstreet101 said:**
> Ahh looks like visuals definetely aren't enabled then. Fraid this is beyond me now. I suspect your onboard graphics chipset isn't up to the job. Try buying a video card and installing the drivers for them. SHould work wonders, not exepensive either. Decent ATI cards are available for as little as £35. But if not then do try someone else, im not all that experienced.

But it worked on my first installation D:

---

### Post by samstreet101 on 2010-07-19
What was your first installation? Was it a full one or was it Wubi or just trial from a live CD? and what version was it?

---

### Post by JonnyOSullivan on 2010-07-19
> **samstreet101 said:**
> What was your first installation? Was it a full one or was it Wubi or just trial from a live CD? and what version was it?

As i said in my first post, visual effects worked on my first installation of Ubuntu Lucid Linux. I liked Linux so much i did a fresh install to give it more space. Now i cant enable visual effects. 

Im not sure if youve seen

> [[IMG]http://img295.imageshack.us/img295/4898/screenshot1be.png[/IMG]]("http://img295.imageshack.us/my.php?image=screenshot1be.png").  Does this mean i have no drivers?

---

### Post by samstreet101 on 2010-07-19
Yes but was it a standard isntallation..i.e just an ISo image burned to a CD or was it a wubi installation? and yes that means you have no proprietary drivers but thats expected if you dont have a video card or a built in wireless card for example.

---

### Post by JonnyOSullivan on 2010-07-19
> **samstreet101 said:**
> Yes but was it a standard isntallation..i.e just an ISo image burned to a CD or was it a wubi installation? and yes that means you have no proprietary drivers but thats expected if you dont have a video card or a built in wireless card for example.

Yes, it was a full, standard installation.

---

### Post by samstreet101 on 2010-07-19
Well if your current one is fairly new and you havent done much to it. It might be worth re-installing again.

---

### Post by JonnyOSullivan on 2010-07-19
> **samstreet101 said:**
> Well if your current one is fairly new and you havent done much to it. It might be worth re-installing again.

Is there a way that i can do a new install without deleting Ubuntu first? Can i install a new Ubuntu over my current Ubuntu?

---

### Post by samstreet101 on 2010-07-19
It would be better to delete it, you can do that using the live cd anyway though. When you select where to install ubuntu to, there is an advanced option that says 'let me choose the partitions' or word to that effect. Choose that and you can format/delete partitions in there

---

### Post by JonnyOSullivan on 2010-07-19
> **samstreet101 said:**
> It would be better to delete it, you can do that using the live cd anyway though. When you select where to install ubuntu to, there is an advanced option that says 'let me choose the partitions' or word to that effect. Choose that and you can format/delete partitions in there

I'll have to do without it then D:

---

### Post by JonnyOSullivan on 2010-07-19
Bump.

---

### Post by javierrivera on 2010-07-19
Open a Terminal, write:

$ compiz --replace

Copy and Paste the output here. If we are lucky there will be some info about why the effects don't start.

---

### Post by JonnyOSullivan on 2010-07-19
> **javierrivera said:**
> Open a Terminal, write:

$ compiz --replace

Copy and Paste the output here. If we are lucky there will be some info about why the effects don't start.

```
WARNING: Application calling GLX 1.3 function "glXCreatePixmap" when GLX 1.3 is not supported!  This is an application bug!
WARNING: Application calling GLX 1.3 function "glXDestroyPixmap" when GLX 1.3 is not supported!  This is an application bug!
compiz (core) - Warn: Exceeded max texture size

Launching fallback window manager
Window manager warning: Invalid WM_TRANSIENT_FOR window 0x4400004 specified for 0x44028d3 ().

```

---

### Post by JonnyOSullivan on 2010-07-19
Bump

---

### Post by lkjoel on 2010-07-19
> **JonnyOSullivan said:**
> ```
WARNING: Application calling GLX 1.3 function "glXCreatePixmap" when GLX 1.3 is not supported!  This is an application bug!
WARNING: Application calling GLX 1.3 function "glXDestroyPixmap" when GLX 1.3 is not supported!  This is an application bug!
compiz (core) - Warn: Exceeded max texture size

Launching fallback window manager
Window manager warning: Invalid WM_TRANSIENT_FOR window 0x4400004 specified for 0x44028d3 ().

```
Do you have Mesa and OpenGL properly installed?

---

### Post by javierrivera on 2010-07-20
> Warn: Exceeded max texture size

Are you using two monitors? Have you increased your resolution? Lowered the video RAM in the BIOS?.

This message is usually related to having a total screen size (usually with multiple monitors) bigger than the maximum size compiz can do with a given graphic card. In my computer the limit is 2048x2048.

---

### Post by JonnyOSullivan on 2010-07-20
> **lkjoel said:**
> Do you have Mesa and OpenGL properly installed?

 How Can i check?

---

### Post by JonnyOSullivan on 2010-07-20
> **javierrivera said:**
> Are you using two monitors? Have you increased your resolution? Lowered the video RAM in the BIOS?.

This message is usually related to having a total screen size (usually with multiple monitors) bigger than the maximum size compiz can do with a given graphic card. In my computer the limit is 2048x2048.

Yes, I have two monitors.

---

### Post by javierrivera on 2010-07-20
This is likely the problem. ¿Total current resolution?.

If you don't know, you can check it with:

```
$ xrandr
```

---

### Post by JonnyOSullivan on 2010-07-20
> **javierrivera said:**
> This is likely the problem. ¿Total current resolution?.

If you don't know, you can check it with:

```
$ xrandr
```

With TWO monitors

```
Screen 0: minimum 320 x 200, current 2048 x 886, maximum 8192 x 8192
VGA1 connected 1024x768+0+0 (normal left inverted right x axis y axis) 410mm x 256mm
   1360x768       59.8  
   1024x768       60.0* 
   800x600        60.3     56.2  
   848x480        60.0  
   640x480        59.9     59.9  
LVDS1 connected 1024x768+1024+118 (normal left inverted right x axis y axis) 367mm x 230mm
   1440x900       59.9 +
   1360x768       59.8  
   1152x864       60.0  
   1024x768       60.0* 
   800x600        60.3  
   640x480        59.9  
HDMI1 disconnected (normal left inverted right x axis y axis)
DP1 disconnected (normal left inverted right x axis y axis)
DP2 disconnected (normal left inverted right x axis y axis)

```



With ONE monitor

```
Screen 0: minimum 320 x 200, current 1360 x 768, maximum 8192 x 8192
VGA1 connected 1360x768+0+0 (normal left inverted right x axis y axis) 410mm x 256mm
   1360x768       59.8* 
   1024x768       60.0  
   800x600        60.3     56.2  
   848x480        60.0  
   640x480        59.9     59.9  
LVDS1 connected 1360x768+0+0 (normal left inverted right x axis y axis) 367mm x 230mm
   1440x900       59.9 +
   1360x768       59.8* 
   1152x864       60.0  
   1024x768       60.0  
   800x600        60.3  
   640x480        59.9  
HDMI1 disconnected (normal left inverted right x axis y axis)
DP1 disconnected (normal left inverted right x axis y axis)
DP2 disconnected (normal left inverted right x axis y axis)

```

---

### Post by javierrivera on 2010-07-20
> current 2048 x 886

I believe that this is too big for compiz by 1 point ;). Maximun supported size in any dimension for intel boards is usually 2047.

Try to go to System -> Preferences -> Screen (or Monitor). Set one of your monitor above the other. Check that it works, you should be able to move the mouse from one monitor to the other going through the bottom (or top) of the screen. Restart. Enable the effects, just select extra on the menu.

If they are working now, we have found the problem. I'm sorry but you have only four solutions:

1) Work with one monitor above the other.
2) Lower one monitor resolution.
3) Upgrade the graphic card.
4) Don't use the effects.

---

### Post by JonnyOSullivan on 2010-07-20
Doesn't work. Even with one Monitor.

---

### Post by javierrivera on 2010-07-20
Hmmm... can you start with only one monitor and then try:

> $compiz --replace

Let's see if there is a different error, or maube just it's keeping the big screen info somewhere. If it spits the same error, please try:

> $cat /etc/X11/xorg.conf

It should return an error: No such file or directory.

---

### Post by JonnyOSullivan on 2010-07-20
Compiz --replace 

```
compiz --replace
WARNING: Application calling GLX 1.3 function "glXCreatePixmap" when GLX 1.3 is not supported!  This is an application bug!
WARNING: Application calling GLX 1.3 function "glXDestroyPixmap" when GLX 1.3 is not supported!  This is an application bug!
compiz (core) - Warn: Exceeded max texture size

Launching fallback window manager
damage_screen (XSR): 1 rects, bounds: 0,0 (1440,900)
expose_area (XSR): 1 rects, bounds: 657,24 (783,27)
expose_area (XSR): 1 rects, bounds: 657,51 (783,410)
expose_area (XSR): 1 rects, bounds: 0,461 (1440,439)
expose_area (XSR): 1 rects, bounds: 0,0 (1440,24)
expose_area (XSR): 1 rects, bounds: 0,24 (657,437)
repair_win (XSR): 1 rects, bounds: 0,0 (1440,900)
configure notify 0 0 1
    extents (XSR): null
    xy (0 0), wh (1440 900)
no extents to damage !
resize_win (XSR): 1 rects, bounds: -9,-7 (1458,918)
configure notify 0 0 1
    extents (XSR): 1 rects, bounds: -9,-7 (1458,918)
    xy (0 0), wh (1440 900)
Inexplicable intersection with new extents!
resize_win (XSR): 1 rects, bounds: -9,-7 (1458,918)
repair_win (XSR): 1 rects, bounds: -9,-7 (1458,42)
configure notify 0 0 0
    extents (XSR): null
    xy (1806 971), wh (4311 115)
no extents to damage !
resize_win (XSR): 1 rects, bounds: 1806,971 (4311,115)
repair_win (XSR): 1 rects, bounds: 1806,971 (4311,115)
repair_win (XSR): 1 rects, bounds: -100,-100 (1,1)
configure notify 0 0 1
    extents (XSR): 1 rects, bounds: -9,-7 (1458,918)
    xy (0 0), wh (1440 900)
Inexplicable intersection with new extents!
resize_win (XSR): 1 rects, bounds: -9,-7 (1458,918)
configure notify 0 0 1
    extents (XSR): 1 rects, bounds: -9,-7 (1458,918)
    xy (0 0), wh (1440 900)
Inexplicable intersection with new extents!
resize_win (XSR): 1 rects, bounds: -9,-7 (1458,918)
repair_win (XSR): 1 rects, bounds: -109,-107 (19,19)
configure notify 0 0 0
    extents (XSR): null
    xy (-1 24), wh (658 437)
no extents to damage !
resize_win (XSR): 1 rects, bounds: -1,24 (658,437)
destroy_win (XSR): 1 rects, bounds: -1,24 (658,437)
configure notify 0 1 1
    extents (XSR): null
    xy (0 24), wh (660 469)
no extents to damage !
resize_win (XSR): 1 rects, bounds: -9,17 (678,487)
configure notify 0 1 1
    extents (XSR): 1 rects, bounds: -9,17 (678,487)
    xy (0 24), wh (660 469)
Inexplicable intersection with new extents!
resize_win (XSR): 1 rects, bounds: -9,17 (678,487)
configure notify 0 1 1
    extents (XSR): 1 rects, bounds: -9,17 (678,487)
    xy (0 24), wh (660 469)
Inexplicable intersection with new extents!
resize_win (XSR): 1 rects, bounds: -9,17 (678,487)
configure notify 0 1 1
    extents (XSR): 1 rects, bounds: -9,17 (678,487)
    xy (0 24), wh (660 469)
Inexplicable intersection with new extents!
resize_win (XSR): 1 rects, bounds: -9,17 (678,487)
configure notify 1 0 0
    extents (XSR): 1 rects, bounds: 1806,971 (4311,115)
    xy (0 923), wh (4311 115)
Inexplicable intersection with new extents!
resize_win (XSR): 3 rects, bounds: 0,923 (6117,163)
    0,971 (6117,67)
    1806,1038 (4311,48)
repair_win (XSR): 1 rects, bounds: 0,923 (4311,115)
paint_all (XSR): 5 rects, bounds: -109,-107 (6226,1193)
    -9,-7 (1458,918)
    0,923 (4311,48)
    0,971 (6117,67)
    1806,1038 (4311,48)
repair_win (XSR): 1 rects, bounds: 2189,961 (57,71)
paint_all (XSR): 1 rects, bounds: 2189,961 (57,71)
repair_win (XSR): 1 rects, bounds: 2189,956 (57,76)
paint_all (XSR): 1 rects, bounds: 2189,956 (57,76)
repair_win (XSR): 1 rects, bounds: 2189,947 (57,85)
paint_all (XSR): 1 rects, bounds: 2189,947 (57,85)
repair_win (XSR): 1 rects, bounds: 2189,942 (57,90)
paint_all (XSR): 1 rects, bounds: 2189,942 (57,90)
repair_win (XSR): 1 rects, bounds: 2189,933 (57,99)
paint_all (XSR): 1 rects, bounds: 2189,933 (57,99)
repair_win (XSR): 1 rects, bounds: 2189,928 (57,104)
paint_all (XSR): 1 rects, bounds: 2189,928 (57,104)
repair_win (XSR): 1 rects, bounds: 2189,923 (57,109)
paint_all (XSR): 1 rects, bounds: 2189,923 (57,109)
configure notify 0 0 1
    extents (XSR): 1 rects, bounds: -9,-7 (1458,918)
    xy (0 24), wh (1440 876)
Inexplicable intersection with new extents!
resize_win (XSR): 1 rects, bounds: -9,-7 (1458,918)
configure notify 0 0 1
    extents (XSR): 1 rects, bounds: -9,17 (1458,894)
    xy (0 24), wh (1440 876)
Inexplicable intersection with new extents!
resize_win (XSR): 1 rects, bounds: -9,17 (1458,894)
repair_win (XSR): 1 rects, bounds: 1013,1 (35,22)
paint_all (XSR): 1 rects, bounds: -9,-7 (1458,918)
expose_area (XSR): 1 rects, bounds: 5,24 (650,1)
expose_area (XSR): 1 rects, bounds: 3,25 (654,1)
expose_area (XSR): 1 rects, bounds: 2,26 (656,1)
expose_area (XSR): 1 rects, bounds: 1,27 (658,2)
expose_area (XSR): 1 rects, bounds: 0,29 (660,459)
expose_area (XSR): 1 rects, bounds: 1,488 (658,2)
expose_area (XSR): 1 rects, bounds: 2,490 (656,1)
expose_area (XSR): 1 rects, bounds: 3,491 (654,1)
expose_area (XSR): 1 rects, bounds: 5,492 (650,1)
repair_win (XSR): 1 rects, bounds: -9,17 (678,487)
determine_mode (XSR): 1 rects, bounds: -9,17 (678,487)
resize_win (XSR): 1 rects, bounds: -15,9 (696,505)
expose_area (XSR): 1 rects, bounds: 0,24 (1440,27)
repair_win (XSR): 1 rects, bounds: -9,17 (1458,894)
repair_win (XSR): 1 rects, bounds: 1,78 (658,410)
repair_win (XSR): 3 rects, bounds: 1837,923 (409,109)
    1837,969 (57,63)
    2189,969 (57,63)
repair_win (XSR): 2 rects, bounds: 230,0 (927,24)
    465,0 (692,24)
paint_all (XSR): 8 rects, bounds: -15,0 (2261,1032)
    465,0 (692,9)
    -15,9 (1172,8)
    -15,17 (1464,497)
    -9,514 (1458,397)
    2189,923 (57,46)
    1837,969 (57,63)
    2189,969 (57,63)
repair_win (XSR): 1 rects, bounds: 1,78 (658,410)
paint_all (XSR): 1 rects, bounds: 1,78 (658,410)
repair_win (XSR): 1 rects, bounds: 1,78 (658,410)
paint_all (XSR): 1 rects, bounds: 1,78 (658,410)
repair_win (XSR): 1 rects, bounds: 1,78 (658,410)


```

cat /etc/X11/xorg.conf 


```
cat: /etc/X11/xorg.conf: No such file or directory

```

---

### Post by JonnyOSullivan on 2010-07-20
Bump

---

### Post by javierrivera on 2010-07-20
> compiz (core) - Warn: Exceeded max texture size

Again... something is too big, so big that it can't fit in the screen. Is there some window than is bigger than 2047?.

All the other lines are metacity (the window manager that is used when compiz is unable to start) problems as it tries to reconstruct the screen. No clue there.

I can reproduce your problem easily in my computer. I just set both my monitors side to side and compiz breaks just like yours. But when I put again one under another, and re-enable de effects everything works again.


I'm missing something here, but I can't right now imagine what. Sorry.

---

### Post by JonnyOSullivan on 2010-07-20
Ok, thanks D:. Any one?:

---

### Post by JonnyOSullivan on 2010-07-20
To the top.

---

### Post by lkjoel on 2010-07-20
Do you have the correct drivers installed?
Go to: [http://forlong.blogage.de/entries/pages/Compiz-Check](http://forlong.blogage.de/entries/pages/Compiz-Check)
to make sure that compiz is correctly installed.

---

### Post by JonnyOSullivan on 2010-07-20
Gathering information about your system...

 Distribution:          Ubuntu 10.04
 Desktop environment:   GNOME
 Graphics chip:         Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
 Driver in use:         intel
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems..../compiz-check: line 488: [: 2502: binary operator expected
           [ OK ]

---

### Post by JonnyOSullivan on 2010-07-20
B-b-b-bump

---

### Post by lkjoel on 2010-07-20
Check this post: [http://ubuntuforums.org/showpost.php?p=9613636&postcount=18](http://ubuntuforums.org/showpost.php?p=9613636&postcount=18)
Download DEtools.tar.gz
Then run in a Terminal window:
```
chmod +x showde
chmod +x DEdetector
DEdetector
```
Then give me the output.
NOTICE: You must download Terminal Enhancements to run it.

---

### Post by JonnyOSullivan on 2010-07-20
> **lkjoel said:**
> 
NOTICE: You must download Terminal Enhancements to run it.

Where from?

---

### Post by lkjoel on 2010-07-20
[https://launchpad.net/terminal-enhancements/+download](https://launchpad.net/terminal-enhancements/+download)
Installation Instructions are available at: [http://essentialsforlinux.blogspot.com/2010/07/terminal-enhancements.html](http://essentialsforlinux.blogspot.com/2010/07/terminal-enhancements.html)

---

### Post by JonnyOSullivan on 2010-07-20
> **lkjoel said:**
> [https://launchpad.net/terminal-enhancements/+download](https://launchpad.net/terminal-enhancements/+download)
Installation Instructions are available at: [http://essentialsforlinux.blogspot.com/2010/07/terminal-enhancements.html](http://essentialsforlinux.blogspot.com/2010/07/terminal-enhancements.html)


```
chmod: cannot access `webinstall.sh': No such file or directory

```

---

### Post by lkjoel on 2010-07-20
> **JonnyOSullivan said:**
> ```
chmod: cannot access `webinstall.sh': No such file or directory

```
Rather, type this in:
```
wget http://launchpad.net/terminal-enhancements/1.0/1.0/+download/webinstall.sh
chmod +x ./webinstall.sh
./webinstall.sh
```
Tell me if it works now.

---

### Post by JonnyOSullivan on 2010-07-20
> **lkjoel said:**
> Rather, type this in:
```
wget http://launchpad.net/terminal-enhancements/1.0/1.0/+download/webinstall.sh
chmod +x ./webinstall.sh
./webinstall.sh
```Tell me if it works now.

```
jonny@jonny-laptop:~$ wget http://launchpad.net/terminal-enhancements/1.0/1.0/+download/webinstall.sh
--2010-07-20 21:56:31--  http://launchpad.net/terminal-enhancements/1.0/1.0/+download/webinstall.sh
Resolving launchpad.net... 91.189.89.223, 91.189.89.222
Connecting to launchpad.net|91.189.89.223|:80... connected.
HTTP request sent, awaiting response... 303 See Other
Location: http://launchpadlibrarian.net/51946176/webinstall.sh [following]
--2010-07-20 21:56:31--  http://launchpadlibrarian.net/51946176/webinstall.sh
Resolving launchpadlibrarian.net... 91.189.89.228, 91.189.89.229
Connecting to launchpadlibrarian.net|91.189.89.228|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 904 [text/x-sh]
Saving to: `webinstall.sh'

100%[======================================>] 904         --.-K/s   in 0s      

2010-07-20 21:56:32 (53.4 MB/s) - `webinstall.sh' saved [904/904]

jonny@jonny-laptop:~$ chmod +x ./webinstall.sh
jonny@jonny-laptop:~$ ./webinstall.sh
Terminal Enhancements Web Installer 0.4
Terminal Enhancements will be installed in your current user
If you are root, it will be installed system-wide.


Installing...

Downloading Terminal Enhancements Archive...--2010-07-20 21:57:00--  http://launchpad.net/terminal-enhancements/1.0/1.0/+download/enhancements.tar.gz
Resolving launchpad.net... 91.189.89.222, 91.189.89.223
Connecting to launchpad.net|91.189.89.222|:80... connected.
HTTP request sent, awaiting response... 303 See Other
Location: http://launchpadlibrarian.net/51946105/enhancements.tar.gz [following]
--2010-07-20 21:57:01--  http://launchpadlibrarian.net/51946105/enhancements.tar.gz
Resolving launchpadlibrarian.net... 91.189.89.229, 91.189.89.228
Connecting to launchpadlibrarian.net|91.189.89.229|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 429 [application/x-tar]
Saving to: `enhancements.tar.gz'

100%[======================================>] 429         --.-K/s   in 0s      

2010-07-20 21:57:01 (33.7 MB/s) - `enhancements.tar.gz' saved [429/429]

Extracting enhancements.tar.gz
Adding lines to ~/.bashrc
newline
./webinstall.sh: line 26: ~/.bashrc: No such file or directory
./webinstall.sh: line 27: ~/.bashrc: No such file or directory
./webinstall.sh: line 28: ~/.bashrc: No such file or directory


Press ENTER to continue

Done!

./webinstall.sh: line 37: ~/.bashrc: No such file or directory

```


Then i do the other code: 


```
jonny@jonny-laptop:~$ chmod +x showde
chmod: cannot access `showde': No such file or directory
jonny@jonny-laptop:~$ chmod +x DEdetector
chmod: cannot access `DEdetector': No such file or directory
jonny@jonny-laptop:~$ DEdetector
DEdetector: command not found

```

---

### Post by lkjoel on 2010-07-20
> **JonnyOSullivan said:**
> ```
jonny@jonny-laptop:~$ wget http://launchpad.net/terminal-enhancements/1.0/1.0/+download/webinstall.sh
--2010-07-20 21:56:31--  http://launchpad.net/terminal-enhancements/1.0/1.0/+download/webinstall.sh
Resolving launchpad.net... 91.189.89.223, 91.189.89.222
Connecting to launchpad.net|91.189.89.223|:80... connected.
HTTP request sent, awaiting response... 303 See Other
Location: http://launchpadlibrarian.net/51946176/webinstall.sh [following]
--2010-07-20 21:56:31--  http://launchpadlibrarian.net/51946176/webinstall.sh
Resolving launchpadlibrarian.net... 91.189.89.228, 91.189.89.229
Connecting to launchpadlibrarian.net|91.189.89.228|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 904 [text/x-sh]
Saving to: `webinstall.sh'

100%[======================================>] 904         --.-K/s   in 0s      

2010-07-20 21:56:32 (53.4 MB/s) - `webinstall.sh' saved [904/904]

jonny@jonny-laptop:~$ chmod +x ./webinstall.sh
jonny@jonny-laptop:~$ ./webinstall.sh
Terminal Enhancements Web Installer 0.4
Terminal Enhancements will be installed in your current user
If you are root, it will be installed system-wide.


Installing...

Downloading Terminal Enhancements Archive...--2010-07-20 21:57:00--  http://launchpad.net/terminal-enhancements/1.0/1.0/+download/enhancements.tar.gz
Resolving launchpad.net... 91.189.89.222, 91.189.89.223
Connecting to launchpad.net|91.189.89.222|:80... connected.
HTTP request sent, awaiting response... 303 See Other
Location: http://launchpadlibrarian.net/51946105/enhancements.tar.gz [following]
--2010-07-20 21:57:01--  http://launchpadlibrarian.net/51946105/enhancements.tar.gz
Resolving launchpadlibrarian.net... 91.189.89.229, 91.189.89.228
Connecting to launchpadlibrarian.net|91.189.89.229|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 429 [application/x-tar]
Saving to: `enhancements.tar.gz'

100%[======================================>] 429         --.-K/s   in 0s      

2010-07-20 21:57:01 (33.7 MB/s) - `enhancements.tar.gz' saved [429/429]

Extracting enhancements.tar.gz
Adding lines to ~/.bashrc
newline
./webinstall.sh: line 26: ~/.bashrc: No such file or directory
./webinstall.sh: line 27: ~/.bashrc: No such file or directory
./webinstall.sh: line 28: ~/.bashrc: No such file or directory


Press ENTER to continue

Done!

./webinstall.sh: line 37: ~/.bashrc: No such file or directory

```
Then i do the other code: 


```
jonny@jonny-laptop:~$ chmod +x showde
chmod: cannot access `showde': No such file or directory
jonny@jonny-laptop:~$ chmod +x DEdetector
chmod: cannot access `DEdetector': No such file or directory
jonny@jonny-laptop:~$ DEdetector
DEdetector: command not found

```
You don't have a ~/.bashrc?
Try:
```
wget http://linuxessentials.googlecode.com/files/DEtools.tar.gz
tar -xf DEtools.tar.gz
wget http://launchpad.net/terminal-enhancements/1.0/1.0/+download/webinstall.sh
sudo chmod +x ./webinstall.sh
sudo echo "" >> /etc/profile
echo "" >> ~/.bashrc
sudo ./webinstall.sh
chmod +x DEdetector
chmod +x showde
sudo chmod +x DEdetector
sudo chmod +x showde
DEdetector
```

---

### Post by JonnyOSullivan on 2010-07-21
> **lkjoel said:**
> You don't have a ~/.bashrc?
Try:
```
wget http://linuxessentials.googlecode.com/files/DEtools.tar.gz
tar -xf DEtools.tar.gz
wget http://launchpad.net/terminal-enhancements/1.0/1.0/+download/webinstall.sh
sudo chmod +x ./webinstall.sh
sudo echo "" >> /etc/profile
echo "" >> ~/.bashrc
sudo ./webinstall.sh
chmod +x DEdetector
chmod +x showde
sudo chmod +x DEdetector
sudo chmod +x showde
DEdetector
```

```
jonny@jonny-laptop:~$ wget http://linuxessentials.googlecode.com/files/DEtools.tar.gz
--2010-07-21 07:41:15--  http://linuxessentials.googlecode.com/files/DEtools.tar.gz
Resolving linuxessentials.googlecode.com... 209.85.227.82
Connecting to linuxessentials.googlecode.com|209.85.227.82|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 434 [application/x-gzip]
Saving to: `DEtools.tar.gz'

100%[======================================>] 434         --.-K/s   in 0.006s  

2010-07-21 07:41:15 (74.1 KB/s) - `DEtools.tar.gz' saved [434/434]

jonny@jonny-laptop:~$ tar -xf DEtools.tar.gz
jonny@jonny-laptop:~$ wget http://launchpad.net/terminal-enhancements/1.0/1.0/+download/webinstall.sh
--2010-07-21 07:41:38--  http://launchpad.net/terminal-enhancements/1.0/1.0/+download/webinstall.sh
Resolving launchpad.net... 91.189.89.222, 91.189.89.223
Connecting to launchpad.net|91.189.89.222|:80... connected.
HTTP request sent, awaiting response... 303 See Other
Location: http://launchpadlibrarian.net/51946176/webinstall.sh [following]
--2010-07-21 07:41:38--  http://launchpadlibrarian.net/51946176/webinstall.sh
Resolving launchpadlibrarian.net... 91.189.89.229, 91.189.89.228
Connecting to launchpadlibrarian.net|91.189.89.229|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 904 [text/x-sh]
Saving to: `webinstall.sh.1'

100%[======================================>] 904         --.-K/s   in 0s      

2010-07-21 07:41:38 (51.9 MB/s) - `webinstall.sh.1' saved [904/904]

jonny@jonny-laptop:~$ sudo chmod +x ./webinstall.sh
[sudo] password for jonny: 
jonny@jonny-laptop:~$ sudo echo "" >> /etc/profile
bash: /etc/profile: Permission denied
jonny@jonny-laptop:~$ echo "" >> ~/.bashrc
jonny@jonny-laptop:~$ sudo ./webinstall.sh
Terminal Enhancements Web Installer 0.4
Terminal Enhancements will be installed in your current user
If you are root, it will be installed system-wide.


Installing...

Downloading Terminal Enhancements Archive...--2010-07-21 07:42:26--  http://launchpad.net/terminal-enhancements/1.0/1.0/+download/enhancements.tar.gz
Resolving launchpad.net... 91.189.89.223, 91.189.89.222
Connecting to launchpad.net|91.189.89.223|:80... connected.
HTTP request sent, awaiting response... 303 See Other
Location: http://launchpadlibrarian.net/51946105/enhancements.tar.gz [following]
--2010-07-21 07:42:26--  http://launchpadlibrarian.net/51946105/enhancements.tar.gz
Resolving launchpadlibrarian.net... 91.189.89.228, 91.189.89.229
Connecting to launchpadlibrarian.net|91.189.89.228|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 429 [application/x-tar]
Saving to: `enhancements.tar.gz'

100%[======================================>] 429         --.-K/s   in 0s      

2010-07-21 07:42:26 (16.9 MB/s) - `enhancements.tar.gz' saved [429/429]

Extracting enhancements.tar.gz
Adding lines to /etc/profile
newline


Press ENTER to continue

Done!

jonny@jonny-laptop:~$ chmod +x DEdetector
jonny@jonny-laptop:~$ chmod +x showde
jonny@jonny-laptop:~$ sudo chmod +x DEdetector
jonny@jonny-laptop:~$ sudo chmod +x DEdetector
jonny@jonny-laptop:~$ DEdetector
DEdetector: command not found
jonny@jonny-laptop:~$ 

```

---

### Post by JonnyOSullivan on 2010-07-21
Bump

---

### Post by JonnyOSullivan on 2010-07-21
Bump.

---

### Post by lkjoel on 2010-07-21
Close that Terminal, then open a new one.
You should see a different prompt.
Then do:
```
chmod +x DEdetector
chmod +x showde
sudo chmod +x DEdetector
sudo chmod +x showde
DEdetector
```

---

### Post by JonnyOSullivan on 2010-07-21
```
jonny@jonny-laptop:~$ chmod +x DEdetector
jonny@jonny-laptop:~$ chmod +x showde
jonny@jonny-laptop:~$ sudo chmod +x DEdetector
jonny@jonny-laptop:~$ sudo chmod +x showde
jonny@jonny-laptop:~$ DEdetector
DEdetector: command not found
jonny@jonny-laptop:~$ 

```

---

### Post by lkjoel on 2010-07-21
```
wget http://linuxessentials.googlecode.com/files/DEtools.tar.gz
tar -xf DEtools.tar.gz
wget http://launchpad.net/terminal-enhancements/1.0/1.0/+download/webinstall.sh
chmod +x ./webinstall.sh
echo "" >> ~/.bashrc
./webinstall.sh
# RESTART COMPUTER
chmod +x DEdetector
chmod +x showde
sudo chmod +x DEdetector
sudo chmod +x showde
DEdetector
```and if it still doesn't work, please give me the output of:
```
cat ~/.bashrc

```and
```
sudo cat /etc/profile
```

---

### Post by javierrivera on 2010-07-21
Not that I know anything about your script, but shouldn't it be?:

> $./DEdetector

After all . is not usually on the path. If DEdetector is in some other dir (in the path) chmod shouldn't work and webinstall will likely need root privileges, or am I missing something?.

---

### Post by lkjoel on 2010-07-21
It is a test to see if TE is correctly installed.
If it isn't, DEtools will not work properly.

---

### Post by javierrivera on 2010-07-21
Yes, nice, but should't he use

./DEdetector

to start it instead of

DEdetector

---

### Post by lkjoel on 2010-07-21
You don't *need* to use:
```
./DEdetector
```
with Terminal Enhancements.

---

### Post by JonnyOSullivan on 2010-07-21
After restart:

> **lkjoel said:**
> ```
wget http://linuxessentials.googlecode.com/files/DEtools.tar.gz
tar -xf DEtools.tar.gz
wget http://launchpad.net/terminal-enhancements/1.0/1.0/+download/webinstall.sh
chmod +x ./webinstall.sh
echo "" >> ~/.bashrc
./webinstall.sh
# RESTART COMPUTER
chmod +x DEdetector
chmod +x showde
sudo chmod +x DEdetector
sudo chmod +x showde
DEdetector
```and if it still doesn't work, please give me the output of:
```
cat ~/.bashrc

```and
```
sudo cat /etc/profile
```

I dont think it worked.

So...

```
 jonny@jonny-laptop:~$ cat ~/.bashrc
# ~/.bashrc: executed by bash(1) for non-login shells.
# see /usr/share/doc/bash/examples/startup-files (in the package bash-doc)
# for examples

# If not running interactively, don't do anything
[ -z "$PS1" ] && return

# don't put duplicate lines in the history. See bash(1) for more options
# ... or force ignoredups and ignorespace
HISTCONTROL=ignoredups:ignorespace

# append to the history file, don't overwrite it
shopt -s histappend

# for setting history length see HISTSIZE and HISTFILESIZE in bash(1)
HISTSIZE=1000
HISTFILESIZE=2000

# check the window size after each command and, if necessary,
# update the values of LINES and COLUMNS.
shopt -s checkwinsize

# make less more friendly for non-text input files, see lesspipe(1)
[ -x /usr/bin/lesspipe ] && eval "$(SHELL=/bin/sh lesspipe)"

# set variable identifying the chroot you work in (used in the prompt below)
if [ -z "$debian_chroot" ] && [ -r /etc/debian_chroot ]; then
    debian_chroot=$(cat /etc/debian_chroot)
fi

# set a fancy prompt (non-color, unless we know we "want" color)
case "$TERM" in
    xterm-color) color_prompt=yes;;
esac

# uncomment for a colored prompt, if the terminal has the capability; turned
# off by default to not distract the user: the focus in a terminal window
# should be on the output of commands, not on the prompt
#force_color_prompt=yes

if [ -n "$force_color_prompt" ]; then
    if [ -x /usr/bin/tput ] && tput setaf 1 >&/dev/null; then
    # We have color support; assume it's compliant with Ecma-48
    # (ISO/IEC-6429). (Lack of such support is extremely rare, and such
    # a case would tend to support setf rather than setaf.)
    color_prompt=yes
    else
    color_prompt=
    fi
fi

if [ "$color_prompt" = yes ]; then
    PS1='${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\$ '
else
    PS1='${debian_chroot:+($debian_chroot)}\u@\h:\w\$ '
fi
unset color_prompt force_color_prompt

# If this is an xterm set the title to user@host:dir
case "$TERM" in
xterm*|rxvt*)
    PS1="\[\e]0;${debian_chroot:+($debian_chroot)}\u@\h: \w\a\]$PS1"
    ;;
*)
    ;;
esac

# enable color support of ls and also add handy aliases
if [ -x /usr/bin/dircolors ]; then
    test -r ~/.dircolors && eval "$(dircolors -b ~/.dircolors)" || eval "$(dircolors -b)"
    alias ls='ls --color=auto'
    #alias dir='dir --color=auto'
    #alias vdir='vdir --color=auto'

    alias grep='grep --color=auto'
    alias fgrep='fgrep --color=auto'
    alias egrep='egrep --color=auto'
fi

# some more ls aliases
alias ll='ls -alF'
alias la='ls -A'
alias l='ls -CF'

# Alias definitions.
# You may want to put all your additions into a separate file like
# ~/.bash_aliases, instead of adding them here directly.
# See /usr/share/doc/bash-doc/examples in the bash-doc package.

if [ -f ~/.bash_aliases ]; then
    . ~/.bash_aliases
fi

# enable programmable completion features (you don't need to enable
# this, if it's already enabled in /etc/bash.bashrc and /etc/profile
# sources /etc/bash.bashrc).
if [ -f /etc/bash_completion ] && ! shopt -oq posix; then
    . /etc/bash_completion
fi


jonny@jonny-laptop:~$ sudo cat /etc/profile
# /etc/profile: system-wide .profile file for the Bourne shell (sh(1))
# and Bourne compatible shells (bash(1), ksh(1), ash(1), ...).

if [ -d /etc/profile.d ]; then
  for i in /etc/profile.d/*.sh; do
    if [ -r $i ]; then
      . $i
    fi
  done
  unset i
fi

if [ "$PS1" ]; then
  if [ "$BASH" ]; then
    PS1='\u@\h:\w\$ '
    if [ -f /etc/bash.bashrc ]; then
    . /etc/bash.bashrc
    fi
  else
    if [ "`id -u`" -eq 0 ]; then
      PS1='# '
    else
      PS1='$ '
    fi
  fi
fi

umask 022

quit() { exit; }
PATH="$PATH:."
PATH="$PATH:./"
PS1="\`if [ \$? = 0 ]; then echo \e[33\;40m\\\^\\\_\\\^\e[0m; else echo \e[36\;40m\\\-\e[0m\\\_\e[36\;40m\\\-\e[0m; fi\` \u \w:\h)  \`if [ \$RANDOM -gt 16382 ]; then printf \"\033[22;31m\"; else printf \"\033[22;34m\"; fi\`"
alias ll='ls -la'
alias cd..='cd ..'
alias vi=vim
alias svi='sudo vi'
alias vis='vim "+set si"'
alias apt-get="sudo apt-get"
alias rm='rm -i'
alias mv='mv -i'
alias cp='cp -i'
alias sha1='openssl sha1'
alias grep='grep --color=auto'
alias df='df -h'

quit() { exit; }
PATH="$PATH:."
PATH="$PATH:./"
PS1="\`if [ \$? = 0 ]; then echo \e[33\;40m\\\^\\\_\\\^\e[0m; else echo \e[36\;40m\\\-\e[0m\\\_\e[36\;40m\\\-\e[0m; fi\` \u \w:\h)  \`if [ \$RANDOM -gt 16382 ]; then printf \"\033[22;31m\"; else printf \"\033[22;34m\"; fi\`"
alias ll='ls -la'
alias cd..='cd ..'
alias vi=vim
alias svi='sudo vi'
alias vis='vim "+set si"'
alias apt-get="sudo apt-get"
alias rm='rm -i'
alias mv='mv -i'
alias cp='cp -i'
alias sha1='openssl sha1'
alias grep='grep --color=auto'
alias df='df -h'
jonny@jonny-laptop:~$ 

```

---

### Post by lkjoel on 2010-07-21
Yes, it did work!
Restart the Terminal, then be sure you are at the correct directory, then type:
```
./DEdetector
```

---

### Post by JonnyOSullivan on 2010-07-21
> **lkjoel said:**
> Yes, it did work!
Restart the Terminal, then be sure you are at the correct directory, then type:
```
./DEdetector
```

  How can i get to the correct directory?

ATM it just says ```
jonny@jonny-laptop:~$ ./DEdetector
./showde: 16: 1: not found
./showde: 16: 0: not found
./showde: 16: 1: not found
./showde: 16: 0: not found
./showde: 16: 1: not found
./showde: 16: 0: not found
./showde: 16: 1: not found
./showde: 16: 0: not found
CLI/PURE

```

---

### Post by JonnyOSullivan on 2010-07-21
```
jonny@jonny-laptop:~$ /home/jonny/DEdetector
./showde: 16: 1: not found
./showde: 16: 0: not found
./showde: 16: 1: not found
./showde: 16: 0: not found
./showde: 16: 1: not found
./showde: 16: 0: not found
./showde: 16: 1: not found
./showde: 16: 0: not found
CLI/PURE
jonny@jonny-laptop:~$ 


```

---

### Post by lkjoel on 2010-07-21
Could you give me the output of:
```
cat DEdetector
```
and
```
cat showde
```

---

### Post by JonnyOSullivan on 2010-07-22
> **lkjoel said:**
> Could you give me the output of:
```
cat DEdetector
```and
```
cat showde
```


```
jonny@jonny-laptop:~$ cat DEdetector
#!/bin/bash
# Shows the DE to the user
./showde
if (($? == 0))
then
echo "An error has occured"
echo "Error code: $?"
exit 127
fi
./showde
if (($? == 1))
then
echo "KDE/QT"
exit 0
fi
./showde
if (($? == 2))
then
echo "GNOME/XFCE/XORG"
exit 0
fi
./showde
if (($? == 3))
then
echo "CLI/PURE"
exit 0
else
echo "An error has occured"
echo "Error code: $?"
exit $?
fijonny@jonny-laptop:~$ cat showde
#!/bin/sh
# Open Source DE detector
# Returns 1 (KDE) 2 (GNOME/XFCE/XORG) 3 (CLI/PURE)
ps -ef | grep '[k]icker' > /dev/null 2>&1
if (($? == 0))
then
exit 1
else
ps -ef | grep 'X ' > /dev/null 2>&1
if (($? == 0))
then
exit 2
else
exit 3
fi
fijonny@jonny-laptop:~$ 

```

---

### Post by lkjoel on 2010-07-22
Now type this in:
```
chmod +x showde
./showde
echo $?
```

---

### Post by JonnyOSullivan on 2010-07-22
```
jonny@jonny-laptop:~$ chmod +x showde
jonny@jonny-laptop:~$ ./showde
./showde: 16: 1: not found
./showde: 16: 0: not found
jonny@jonny-laptop:~$ echo $?
3

```

---

### Post by javierrivera on 2010-07-22
Again, I don't understand what you are trying to achieve, but I'll take a risk again, don't hit me too strong if I'm wrong.

If you are using bash-only syntax, you should probably change the first line to:

```
#!/bin/bash
```

Or use a more shell neutral syntax like:

```
if [ $? -eq 0 ]
```

Both solutions work nice on my machine (with fish as default shell).

---

### Post by JonnyOSullivan on 2010-07-22
> **javierrivera said:**
> Again, I don't understand what you are trying to achieve, 

That makes two of us.

---

### Post by lkjoel on 2010-07-22
The script will detect if you are using CLI/XVESA (below minimum requirements) or XORG/KICKER (Requirements)

---

### Post by javierrivera on 2010-07-23
Then he's running Xorg. 

```
./showde: 16: 1: not found
./showde: 16: 0: not found

```

That 1 is likely the value of $? when checking for '[K]icker', the 0 on the second line the value of $? when checking for 'X '.

---

### Post by JonnyOSullivan on 2010-07-23
So, this means?

---

### Post by javierrivera on 2010-07-23
That you are not using the VESA mode, AFAIK. That means that your computer is loading the graphic drivers for your card.

But maybe lkjoel can get something more useful from this.

---

### Post by lkjoel on 2010-07-23
It looks like you are running XVESA.
It outputs 3, which means that you are not running XORG or KDE.

---

### Post by JonnyOSullivan on 2010-07-24
Bbuummpp

---

### Post by javierrivera on 2010-07-26
> **lkjoel said:**
> It outputs 3, which means that you are not running XORG or KDE.

It just means that there is an error in the if statements. So it takes the else route.

---

### Post by lkjoel on 2010-07-26
[https://help.ubuntu.com/community/CompositeManager/CompizFusion](https://help.ubuntu.com/community/CompositeManager/CompizFusion)
Try that page.

---

### Post by lkjoel on 2010-08-06
Check this guide out: [http://openubuntu.com/index.php/topic,294.0.html](http://openubuntu.com/index.php/topic,294.0.html)
Follow the instructions.
Download the attachment into your home folder.
Then type this in a Terminal. (This time it will work!)
```
cd ~
gunzip DEtools.tar.gz
tar -xf DEtools.tar
chmod +x DEdetector
chmod +x showde
DEdetector
```Then could you output me the results?

---

### Post by JonnyOSullivan on 2010-08-07
> **lkjoel said:**
> Check this guide out: [http://openubuntu.com/index.php/topic,294.0.html](http://openubuntu.com/index.php/topic,294.0.html)
Follow the instructions.
Download the attachment into your home folder.
Then type this in a Terminal. (This time it will work!)
```
cd ~
gunzip DEtools.tar.gz
tar -xf DEtools.tar
chmod +x DEdetector
chmod +x showde
DEdetector
```Then could you output me the results?


```
jonny@jonny-laptop:~$ cd ~
jonny@jonny-laptop:~$ gunzip DEtools.tar.gz
jonny@jonny-laptop:~$ tar -xf DEtools.tar
jonny@jonny-laptop:~$ chmod +x DEdetector
jonny@jonny-laptop:~$ chmod +x showde
jonny@jonny-laptop:~$ DEdetector
GNOME/XFCE/XORG
jonny@jonny-laptop:~$ 

```

And visual effects still doesnt work D:

---

### Post by lkjoel on 2010-08-08
It wasn't supposed to help visual effects.
It was just supposed to tell me if your computer could run it!
It looks like it can.
Go to the synaptic package manager (System->Administration->Synaptic) then search for compiz.
Select every single package that is installed (green checkmark) then click on the checkmark of one of them, then select: "Mark for complete removal".
Click on Apply, then click on Apply again.
After it is removed, close synaptic.
Then type this in a terminal window:
```
apt-get install compiz compizconfig-settings-manager compiz-fusion-plugins-extra compiz-fusion-plugins-unsupported emerald simple-ccsm
```
Do not worry about no sudo.
That is a benefit of Terminal Enhancements.
Restart your computer, then when you log back into GNOME, type this in:
```
compiz --replace
```
Once you see your windows again, you can close the Terminal.

---

### Post by lkjoel on 2010-08-17
So are you using two monitors?

---

