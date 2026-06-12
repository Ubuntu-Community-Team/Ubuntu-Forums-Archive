---
title: "how to make xorg see my HDMI connection as a secondary one and the DVI as the main?"
date: 2010-07-10
forum: General Help
---

### Post by Miki800 on 2010-07-10
[SIZE="1"](Previous title - "*how to make xorg see my HDMI connection as a secondary one and the DVI as the main?*")[/SIZE]

right now it is impossible to apply any changes using 'gnome-display-properties'
it is possible to make changes using the gui of this command line 'amdxdg-su -c amdcccle' (yes I'm using ATI)

these are the connections my ATI card offers me:
HDMI, DVI and a VGA connection I do not use

my screen is connected to the DVI connection - what I want to be the main screen
my television is connected to the HDMI connection - what I'd like to be the secondary screen

I would rather that by default they would both be cloned always.


I can configure that using 'amdxdg-su -c amdcccle' but after a restart and a login my screen gets disabled and all I have left is my HDMI connection - to the far away television.

if I disconnect the HDMI connection prior to logging in then then DVI connection still remains enabled, afterwards I can reconnect the HDMI connection and reapply clone-mode.



My goal is to force the xorg configuration to acknoledge the fact that I demand the two screens to be only in cloned mode,
or if thats impossible before logging in then I want to force xorg to understand that my DVI connection would be my main connection and not the secondary one when it comes to deciding which single screen gets enabled after a login.


here is my xorg.conf file:


```

Section "ServerLayout"
	Identifier     "amdcccle Layout"
	Screen      0  "amdcccle-Screen[1]-0" 0 0
EndSection

Section "Files"
EndSection

Section "Module"
	Load  "glx"
EndSection

Section "Monitor"
	Identifier   "0-DFP1"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
	Option	    "TargetRefresh" "60"
	Option	    "Position" "0 0"
	Option	    "Rotate" "normal"
	Option	    "Disable" "false"
	Option	    "PreferredMode" "1680x1050"
EndSection

Section "Monitor"
	Identifier   "0-DFP2"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
	Option	    "TargetRefresh" "60"
	Option	    "Position" "0 0"
	Option	    "Rotate" "normal"
	Option	    "Disable" "false"
	Option	    "PreferredMode" "1680x1050"
EndSection

Section "Device"
	Identifier  "Default Device"
	Driver      "fglrx"
EndSection

Section "Device"
	Identifier  "amdcccle-Device[1]-0"
	Driver      "fglrx"
	Option	    "Monitor-DFP1" "0-DFP1"
	Option	    "Monitor-DFP2" "0-DFP2"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
	Identifier  "amdcccle-Device[1]-1"
	Driver      "fglrx"
	Option	    "Monitor-DFP2" "0-DFP2"
	Option	    "Monitor-DFP1" "0-DFP1"
	BusID       "PCI:1:0:0"
	Screen      1
EndSection

Section "Screen"
	Identifier "Default Screen"
	DefaultDepth     24
EndSection

Section "Screen"
	Identifier "amdcccle-Screen[1]-0"
	Device     "amdcccle-Device[1]-0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "Screen"
	Identifier "amdcccle-Screen[1]-1"
	Device     "amdcccle-Device[1]-1"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

```

I'd love to get assistance as to which lines I have to change into what to achieve what I want, thank you very much :)


**_edit: update for those who do not want to read everything to know whats the current conclusion -_**

well, so far so fail, found three possible ways to solve this, all three possible solutions failed accomplishing anything useful related to this issue:

* ati has a tool called aticonfig, it is a command line tool and it looks like it can set cloned (also know as mirrored) mode
but it will fail doing so because it insists RandR (which is required to run compiz) conflicts with it
 - **WHICH IS A WRONG CONCLUSION** - since I am right now in cloned mode with compiz enabled

* ati has a gui program called amdcccle, can be launched with administration (root <-- bad *** user that can actually apply and supposed to be able to save configurations locally) privileges by running: ```
amdxdg-su -c amdcccle
```
it can, and **WILL WORK** for changing resolution and screens configuration, the only problem with it is that it refuses to save the already successfully applied changes to the permanent X configuration file - /etc/X11/xorg.conf
so it can not save changes - meaning changes has to be made repeatedly again and again after every restart if same configurations are wanted again.

* there is a way in ubuntu to save the current configuration of everything or a few things (I say thing because I do not know yet what exactly can be saved)
there used to be a session manager that could save the current session and by saying that I mean IT COULD SAVE THE CURRENT X CONFIGURATION PERMANENTLY!
the problem is... -_-' [COLOR="Red"]*session manager got removed from ubuntu a few versions ago*[/COLOR]
right now it's supposed replacement is available through the menu gui System-->Preferences-->Startup Applications (doesn't sound like "session" in it does it?)
but the name of the application is "gnome-session-properties"

anyways it has this "other" feature which is suppose to contain the missing ability of the previous session-manager, accessible through the gui Options tab --> remember current running applications <-- fails to do anything related to the current X settings and saving it permanently to /etc/X11/xorg.conf

---

### Post by dcstar on 2010-07-11
> **Miki800 said:**
> right now it is impossible to apply any changes using 'gnome-display-properties'
it is possible to make changes using the gui of this command line 'amdxdg-su -c amdcccle' (yes I'm using ATI)

these are the connections my ATI card offers me:
HDMI, DVI and a VGA connection I do not use
.........

The DVI/HDMI is one output, the VGA is the second output.

You can use **either** DVI or HDMI at one time but not both simultaneously.

When you card detects a HDMI connection it diverts the video output from the DVI connector to the HDMI connector.

Get a DVI-VGA adaptor (or connect you monitor using a VGA cable) and then you can have two video connections.

I had the exact same issue with my ATI video a few weeks ago when I finally got a HDMI cable to connect up my TV to the PC.

---

### Post by Miki800 on 2010-07-12
> **dcstar said:**
> The DVI/HDMI is one output, the VGA is the second output.

You can use **either** DVI or HDMI at one time but not both simultaneously.

WRONG :) I can use both as extended screens or cloned screens.

thats just the way, it is what it is.
as to your conclusion - maybe you concluded that because of my xorg.conf file above.


if so, the only way that you could possibly be helpful is by telling me how you figured that conclusion out.
anyways it is wrong since I actually **can** use both screens simultaneously. 

> **dcstar said:**
> 
When you card detects a HDMI connection it diverts the video output from the DVI connector to the HDMI connector.

up to the stage when I actually pass the login screen and wait for my logged account to load the desktop - I have cloned screens and I see the output on both screens, I mean on both the television and the screen

> **dcstar said:**
> 
Get a DVI-VGA adaptor (or connect you monitor using a VGA cable) and then you can have two video connections.

I had the exact same issue with my ATI video a few weeks ago when I finally got a HDMI cable to connect up my TV to the PC.
yes this might be a solution but it is not a solution of the way I am interested in. thanks anyways for offering that.


heck, if I can undo the "DE-CLONING" of the already-perfectly-cloned screens by manually using the GUI mentioned above,
I bet that there should be a script that would be able to do the very same thing for me when I finally log in without any stupid prompts at all!

I mean come on people, this is Linux, we have scripts for everything!
I just don't feel like using an adapter where my PC is located, it is pretty crowded where it's placed as it is up against the wall, there won't be enough room for the adapter and the cable.

this still needs solving, please assist.

---

### Post by 01001101 on 2010-07-12
Let's just see if I have you correct:
You have a multi-screen graphics card and you want to keep the multi screen settings. To do this you go to the nvidia x server settings application and try to configure your x server display. When you click save to x configuration file you get a failure message.

If this is the problem that's happening then I know exactly why, but if it isn't it may be for the same reason, so read my suggestion anyway.

First of all this problem would only be a problem if you are using ubuntu 9.04 or lower. If you're not, then I'm a blabbering idiot and you shouldn't listen to me. If you are then, read on.

I had the same problem with my xorg.conf file. The problem is that its in a folder that has permissions denied.




The first thing that you could do, is update to ubuntu 10.04. This is my top recommendation. Ubuntu 10.04 looks better and it's added some cool new features. 

You can upgrade by going to system >> update manager.

If you don't want to update you could modify these files manually. Access the document through terminal (Applications >> Accessories >> Terminal) and type "gksudo nautilus." this will open a window that will allow all permissions. Use that window to go to "etc/x11/xorg.conf" Open the file, delete the text, and paste your xorg text in the file. Save it and you're done.

---

### Post by Miki800 on 2010-07-13
* post deleted *

---

### Post by Miki800 on 2010-07-16
* BUMP *

> **01001101 said:**
> Let's just see if I have you correct:
You have a multi-screen graphics card and you want to keep the multi screen settings. To do this you go to the **_[SIZE="4"]nvidia[/SIZE]_** x server settings application
I have an ATI card :)

> **01001101 said:**
> and try to configure your x server display. When you click save to x configuration file you get a failure message.

when I try to use the gnome-built-in display manager configuration editor I get some sort of failure message saying that currently something else is in charge of making such changes

I can't remember the exact string currently because I am away from my desktop


> **01001101 said:**
> 
If this is the problem that's happening then I know exactly why, but if it isn't it may be for the same reason, so read my suggestion anyway.

First of all this problem would only be a problem if you are using ubuntu 9.04 or lower.

I'm using ubuntu lucis 10.4

> **01001101 said:**
> If you're not, then I'm a blabbering idiot and you shouldn't listen to me.
don't be so hard on yourself :) I appreciate every one who tries to help! really!!

> **01001101 said:**
>  If you are then, read on.

I had the same problem with my xorg.conf file. The problem is that its in a folder that has permissions denied.


well, I can edit the xorg.conf file with `gksudo gedit /etc/X11/xorg.conf` if I'd like to, and save as well,
I bet chmodding 770 to the folder and files might make such problems disappear

> **01001101 said:**
> 

The first thing that you could do, is update to ubuntu 10.04. This is my top recommendation. Ubuntu 10.04 looks better and it's added some cool new features. 

You can upgrade by going to system >> update manager.

If you don't want to update you could modify these files manually. Access the document through terminal (Applications >> Accessories >> Terminal) and type "gksudo nautilus." this will open a window that will allow all permissions. Use that window to go to "etc/x11/xorg.conf" Open the file, delete the text, and paste your xorg text in the file. Save it and you're done.

well, that is a great tip - if one knows exactly what needs to be put in the xorg.conf file


giving tips about how to edit the file does not really help one who doesn't know what to put in that file to achieve one's goals.

editing it isn't the problem.

thanks for the attempt though :)

still needs help solving this


* BUMP *

---

### Post by hawthornso23 on 2010-07-17
If you have an ATI card then perhaps aticonfig is what you want. Run
```
aticonfig
```
and read the various exciting options available for configuring multiple screens.

---

### Post by dcstar on 2010-07-17
> **01001101 said:**
> Let's just see if I have you correct:
You have a multi-screen graphics card and you want to keep the multi screen settings.
........

He may well have a multi-screen card but he refuses to use the "other" output which is the VGA connector.

Cards with only one DVI & HDMI connector usually only have one digital video output source, it is shared between the two physical connector types and cannot be separated. The only separate output is the analogue VGA output.

HDMI to DVI adaptors work by connecting the digital video signal to the pins reserved for that function on the DVI-D connector, the connector on the card does the same thing. Some cards with a DVI and HDMI connector deliberately have them so close that you cannot plug both connectors in at the same time, just to get through the message that you can only really use one at a time.

True dual-head cards have two DVI and/or HDMI connectors which can be used separately, but these cards cost more because of the extra hardware required.

---

### Post by Miki800 on 2010-07-23
* post deleted *

---

### Post by Miki800 on 2010-07-24
> **hawthornso23 said:**
> If you have an ATI card then perhaps aticonfig is what you want. Run
```
aticonfig
```
and read the various exciting options available for configuring multiple screens.

[SIZE="1"]thank you all for the attempts to help and thanks hawthornso for telling me that I need to keep looking for the solution myself in the aticonfig command.[/SIZE]

it seems to have some bug in it when I try the clone option:
> 
root@ubuntu:/etc/X11# aticonfig --dtop clone
_**Error: Options, e.g. --dtop and --desktop-setup, are not supported when RandR 1.2 is enabled!**_
Using xorg.conf
Saved back-up to xorg.conf.fglrx-3

> 
root@ubuntu:/etc/X11# aticonfig --dtop mirror
**_Error: Options, e.g. --dtop and --desktop-setup, are not supported when RandR 1.2 is enabled!_**
Using xorg.conf
Saved back-up to xorg.conf.fglrx-4

```

root@ubuntu:/etc/X11# aticonfig --help
Usage: aticonfig [OPTION] ...
Parses an existing X-Server configuration file and modifies it to operate with
ATI products.

The following command-line options can be invoked as parameters:

ATI Initial Configuration:
  --initial
        Generate a default ATI device section in the configuration file which
        is capable of loading the fglrx driver.
  --initial=dual-head
        Same as '--initial' but generate a basic dual head configuration file.
  --initial=check
        Identifies if the fglrx driver is present in configuration file.

Screen-Related Options:
  --dtop, --desktop-setup=STRING
        Change the desktop setup for multiple display adapters.
        STRING can be one of:
            single              1 screen, second dark
            mirror              2 screens - same content, identical
                                refresh rate/resolution
                                Note: This option is NOT supported with Avivo
            clone               2 screens - same content, allows for
                                different refresh rates/resolutions
        Note:  This option is not valid if '--initial=dual-head' is specified.

```

but giving up on RandR meaning no Compiz right?
well thats out of the question, stupid and ridicules since I am in manually-set cloned mode right now with compiz enabled successfully.
why should I give up compiz just to use this tool?


I tried another way to google my problem and I checked this out:

[http://ubuntuforums.org/showthread.php?t=794551](http://ubuntuforums.org/showthread.php?t=794551) - CCC ignores the need to save xorg.conf, solution might be to save current user session so it gets always re-applied
and found this as well:
[http://ubuntuforums.org/showthread.php?t=1149873](http://ubuntuforums.org/showthread.php?t=1149873) -session manager is gone from the few last versions of ubuntu, removed and no way to save session anymore (only to save all current running windows information)


seems like these people have the EXACT same problem as I do -
like me they can not save forever the applied changes (the manually set amdcccle of cloned screens is not saved through sessions)

and session-manager for ubuntu-gnome has been removed a few versions ago of ubuntu (now I'm using 10.04, seems like it went MIA since 9.04 I think)

and without a way to save my X session current settings to the general Xorg configuration that lasts through sessions..

I can have no solution for my problem using sessions or aticonfig


**[COLOR="Red"][SIZE="4"]this problem still needs solving[/SIZE][/COLOR] please help!**

* *BUMP* *

---

