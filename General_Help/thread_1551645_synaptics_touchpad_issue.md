---
title: "synaptics touchpad issue"
date: 2010-08-12
forum: General Help
---

### Post by ptoche on 2010-08-12
This is my first post. I'm completely new to this.

I just got an HP-DV6-3048TX, a laptop that comes with a synaptics touchpad. I have Windows 7 Pro 64 bits on one partition and Kubuntu 10.4 on another partition, with Kubuntu intalled from DVD on the "largest available diskspace" (thus letting Kubuntu create the required extended partitions automatically). So far, I cannot report too many problems, except related to my attempts to configure the touchpad.

I hate the touchpad. It's got several problems, let me list them:

1) it's big, so my palm and fingers touch it repeatedly while typing, sending the pointer all over the place,

2) the left- and right-click buttons are made of touchpad material, so that when I click the pointer is first displaced as though I had stroked the touchpad, with the result that I miss the target most of the time.

3) I have found it quite difficult to configure. 

I have so far tried to play around with the settings in:
System Settings / Keyboard & Mouse / Touchpad 
System Settings / Keyboard & Mouse / Mouse

I don't seem to be able to find an optimal combination of parameters. I'd appreciate if someone would share their optimal choice of options, especially the Advanced Settings in the Mouse Settings. (In Windows7 I did find a nearly suitable combination, disabling scrolling, tapping, and so on, while making the mouse very insensitive but the speed fast, weird but second best -- first best being the old-fashioned touchpad with mechanical buttons) 

I just can't find the right combination of options. Let me list my current selections (arrived at by a random process). 
Advanced Mouse Settings:
pointer acceleration: 2.0x
pointer threshold: 4 pixels
double-click interval: 200 msec
drag start time: 200 msec
drag start distance: 4 pixels
mouse wheels scrolls by: 5 lines
Touchpad Settings:
General: on,
Sensitivity: near the middle, slightly closer to "low"
Scrolling: off
Tapping: off

The result is a nightmare: pointer moves all over the place, e.g. if I have multiple tabs opened in my browser and hover my pointer over one of the tabs while preparing my left finger to click the tabs start to switch frenetically, e.g. if I try to control the cursor to the right of this browser window it will settle either for the top or the bottom but won't stay in an intermediate position. Depressing.

I am aware of the existence of touchfreeze, which may solve my problems with touching the touchpad while typing. Unfortunately after installing it all sorts of things started to go wrong. So I have uninstalled it now. I know there's another utility that does what touchfreeze does (the name will get back to me). But the more pressing problem I have is unrelated to this issue. It's a "mouse out of control" issue.

okay, so someone will ask, "what sort of thing went wrong exactly?" In a word, things like this:

```

patrick@patrick-linux:~$ kdesudo kate
kdesudo(5462): ""CurrencyIntroducedDate" - conversion of "" to QDate failed" " (wrong format: expected 3 items, got 1)" 

repeated maybe 50 times

kdesudo(5462): ""CurrencyIntroducedDate" - conversion of "" to QDate failed" " (wrong format: expected 3 items, got 1)" 
QInotifyFileSystemWatcherEngine::addPaths: inotify_add_watch failed: No such file or directory
QFileSystemWatcher: failed to add paths: /root/.config/ibus/bus
Bus::open: Can not get ibus-daemon's address. 
IBusInputContext::createInputContext: no connection to ibus-daemon 
kate(5467)/kdecore (services) KMimeTypeFactory::parseMagic: Now parsing  "/usr/share/mime/magic"
patrick@patrick-linux:~$ ^C

```

The same error occurs on other software whenever I run kdesudo or simply sudo (which you're not supposed to). But if I open kate by clicking on its icon, no errors reported.

Now the above error code may not be related to my installing touchfreeze, but I can't think of anything else I did that could have messed things up this way. Except, of course, running automatic updates.

Back to the synaptics touchpad and basic pointer control. I'm not sure I have the correct or latest driver installed. I don't know how to check in kubuntu. I looked for a xorg.conf file in /etc/X11, because I read somewhere that's a file from which you can customize the touchpad, but I don't have an xorg.conf file in /etc/X11. I do have xorg.conf.failsafe instead, and it has the following entry:

```

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"vesa"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection


```

I don't know if this is the relevant settings file, but I have a feeling that vesa may not be the correct driver. If so, then, how should I proceed to install the correct driver?

I'd appreciate any pointers!

---

### Post by ptoche on 2010-08-12
In the Mouse System Settings, with the Advanced Tab open, if I hover the pointer above the boxes with one finger, nothing happens, but if my palm or another finger touches the touchpad at the same time, then the numbers inside the boxes start to change frantically. It's as if two contacts of the touchpad were interpreted as some sort of tap to click -- but I have tapping disabled, how can this be?

---

