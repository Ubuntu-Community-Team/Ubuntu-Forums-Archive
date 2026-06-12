---
title: "Maverick FGLRX screen corruption"
date: 2011-04-05
forum: General Help
---

### Post by Lolpanda on 2011-04-05
Only have a few minutes to right this so sorry if its rushed.

Using FGLRX (latest from Maverick repos), ubuntu kernel (pae) ubuntu xorg. All updated. Was in Libreoffice (installed from ppa) and I noticed on some dialogue boxes the screen was corrupted, typically dashed white and black lines, sometimes inverted colors. At first I thought this was a libreoffice problem until I opened up a terminal (screenshot below, you can see it in the menu area of terminal)

my xorg.conf:

```

Section "Screen"
	Identifier	"Default Screen"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Default Device"
	Driver	"fglrx"
EndSection
```


Direct Rendering reports: Yes

glxgears is showing 3000+ FPS

Its a Radeon HD 3200 (integrated) card. Honestly I'm really not sure where to start with diagnosing this.

---

### Post by Lolpanda on 2011-04-06
Small bump

---

### Post by Krytarik on 2011-04-06
This indeed hurts your eyes!

First, upgrade the video driver through Ubuntu-X-Swat PPA if you haven't done so already, it offers more recent drivers than the offical repos:
[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates]("https://launchpad.net/%7Eubuntu-x-swat/+archive/x-updates")
```
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update
sudo apt-get upgrade
```Then create a new proper xorg.conf:
```
sudo aticonfig --initial -f
```Then reboot/relogin.

Greetings.

---

### Post by Lolpanda on 2011-04-06
Will do. Had been trying to avoid the xorg ppa only because of xorg updates that would break comparability with catalyst/fglrx, but we'll give it a shot, can always ppa-purge later.

Doing a massive download right now so it'll be a few before I can reboot; will reply back with any improvements

---

### Post by Krytarik on 2011-04-06
> **Lolpanda said:**
> Will do. Had been trying to avoid the xorg ppa only because of xorg updates that would break comparability with catalyst/fglrx, but we'll give it a shot, can always ppa-purge later.
This IS NOT the Xorg-Edgers' PPA, if you are referring to those, those doesn't even offer the fglrx driver. No, this is Ubuntu-X-Swat's PPA, the packages they are providing don't do major changes to your system, they are just a few video driver packages, like you can see when you visit the PPA's site. And yeah, knowing how to purge the PPA if necessary is always good.

---

### Post by Lolpanda on 2011-04-07
Still no luck. Let me try something from the the Arch Linux Wiki (damn it if those guys & Gentoo don't have the best Wiki's in the entire Linux Ecosystem haha)

Screenshot below -- you can see it in the top panel around the menu and the clock. That was from having JUST rebooted and JUST updating fglrx & remaking xorg.conf

Screenshot attatched, xorg.conf repost (Its longer this time. I guess Jockey doesn't do aticonfig --initial -f when you use the Hardware Drivers app, cuz you can compare the two from this post and my first post, first post was Jockey's, second is --initial -f):

```
eric@desktop:~$ cat /etc/X11/xorg.conf
Section "ServerLayout"
	Identifier     "aticonfig Layout"
	Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Module"
	Load  "glx"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]-0"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]-0"
	Driver      "fglrx"
	BusID       "PCI:1:5:0"
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]-0"
	Device     "aticonfig-Device[0]-0"
	Monitor    "aticonfig-Monitor[0]-0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

eric@desktop:~$
```

---

### Post by Krytarik on 2011-04-07
Does this issue also occur if you run Metacity instead of Compiz (which I assume you are running)?:
- press Alt+F2
- enter:
```
metacity --replace
```Btw., you can enable compositing in Metacity by running this command:
```
gconftool-2 /apps/metacity/general/compositing_manager --type bool --set true
```

---

### Post by Lolpanda on 2011-04-08
And down the rabbit hole we go....

Rebooted, sound works... monitor errrored out with "Cannot display this video type" or something similar (I could have sworn I made a thread with that same problem like 2 years ago on a different ubuntu version...) 

At first I thought it was the xorg.conf (the new one) so I swapped the one that aticonfig made, out with the one that jockey made when I installed the drivers. Guess what, same problem -.- Soooo a configuration that worked 3 days ago, no longer works. And nothing's changed.

I could have SWORN i had told Gnome to run metacity --replace in Startup Applications, on every boot but for some reason it wasn't listed there.


If you're curious, both xorg.confs are listed above in the various posts. Right now im running on either the radeon or VESA driver and its not correctly picking..or even listing my monitor's resolution under Preferrences. I'm starting to wonder what application is ACTUALLY bugging out. Xorg, Metacity/Gnome, or FGLRX

Starting to think its Fglrx or my xorg.confs. 

Vesa/Radeon I don't have problems with (Corruption wise). But that doesn't make sense, because I had Maverick installed on here before, also Fedora 14, with fglrx, and Arch with fglrx, all worked fine without corruption. And this would be the second time where I've installed an Ubuntu version when it first came out, everything worked fine, then I switched to a different distro and when I came back I had graphic corruption (always the same type of corruption, dashed lines and warped images)

Happened with 10.04, and now happening with 10.10, its seriously like that whoever is the maintainers on these packages aren't watching to see if bumping up versions by more than 1 is introducing bugs. Such as if you had 10.10 when it first came out, and kept up the updates moving from say fglrx 10.5.6 (base version) then 10.5.7 (update) then 10.5.8 (update) etc etc, but aren't checking to see if bugs pop up when you jump from 10.5.6 to 10.7.8 in a single update, like what would happen if someone leaves the distro and comes back to it using the same CD

---

### Post by Krytarik on 2011-04-08
First, I haven't seen a general issue with similar corruptions like this. So, it seems to be more confined to your specific system.

Also, what is actually the answer to my question, do you have this corruption also if you run Metacity?

More often than not Compiz is the cause of this kind of issues, and numerous other ones.
But usually, one is able to get it working at last.

If you want to always run Metacity instead, you can either
- switch "Appearance -> Visual Effects" to "None"
- or if that doesn't work, modify the related Gconf keys:
```
gconftool-2 /desktop/gnome/applications/window_manager/current --type string --set /usr/bin/metacity
gconftool-2 /desktop/gnome/applications/window_manager/default --type string --set /usr/bin/metacity

```The value for Compiz is "/usr/bin/compiz".

---

### Post by Lolpanda on 2011-04-08
Then thats really unfortunate, and yes it would seem I am running metacity (not as a compositing manager) because I had gone and set Visual Effects to none to get a few extra FPS out of games





Edit: and We're back on track with the corruption...

brought up terminal

sudo aticonfig --initial   (With NO xorg.conf even existing, it had to create its own)
sudo reboot

Ubuntu came up fine to the desktop (monitor didnt error out saying it didnt support the video output) But I still had corruption when using metacity as the default window manager with compositing disabled. Could this possibly be from the theme I'm using? Its Bisigi's "Airlines" theme

---

### Post by Krytarik on 2011-04-08
> **Lolpanda said:**
> Could this possibly be from the theme I'm using? Its Bisigi's "Airlines" theme
Yeah, may be so. Did you try another theme!?

Also, I forgot to mention that the cause may also be the fglrx driver.

---

### Post by Lolpanda on 2011-04-08
Aaaand things just took a weird turn. So I gotta explain this in an odd way. 

If

Window Manager = Compiz. (Been jumping between metacity and compiz with fusion-icon) And Visual Effects are set to Normal or Extra: Graphics **don't** get corrupted / distorted.

If

Window Manager = Metacity and Visual Effects are set to none and metacity is NOT told to be a Compositing Manager under gconf /apps/metacity/general. Graphics get Distrted.

If

Window Manager = Metacity and Visual Effects are set to none and metacity IS told to be a Compositing Manager under gconf /apps/metacity/general. Graphics **don't** get distorted. 


So it has something to do with how Metacity handles graphics when it doesn't have access to a compositing manager, maybe Indirect / Direct Rendering? 


If Any Devs have been following this thread, consider this a bug report against Metacity / Fglrx as I dont have a launchpad account to report this.

My only real issue is this:

glxgears:


Metacity without compositing: 3,000 FPS (Visual Effects: none)
Compiz: 2,000 FPS (Visual effects: Normal)
**Metacity WITH compositing: 500 FPS**  (Visual effects: none) <---- WTF?!

---

### Post by Krytarik on 2011-04-08
The conclusion is then to run either
a) Metacity with compositing enabled, which runs faster/more consistent anyway, or
b) Compiz.

> **Lolpanda said:**
> 
If Any Devs have been following this thread, consider this a bug report against Metacity / Fglrx as I dont have a launchpad account to report this.
The devs usually don't come here and/or aren't following every thread. And even if so, they wouldn't take this as bug report. So, if you want to report this as a bug, create a launchpad account and report it as usual.

---

