---
title: "Mouse buttons have changed, how to configure?"
date: 2009-09-02
forum: General Help
---

### Post by jon.mithe on 2009-09-02
Hi,

I downloaded a bunch of updates using the update manager and it has reconfigured my mouse buttons.

I have a logitech mx wireless mouse, and it has one of those scroll wheels that you can also click left, right + down.

It used to be clicking left / right scrolled on horizontal bars but now it adjusts the volume.

Anyone know how to reconfigure the left / right scroll button to scroll left / right?

I tried looking in the mouse preferenes but nothing.  Tried searching around these forums and google for help, but most of what I see seems out of date or reconfiguring xorg, which I thought with the ATI drivers is a futile effort.

Found a link here [https://help.ubuntu.com/community/ManyButtonsMouseHowto](https://help.ubuntu.com/community/ManyButtonsMouseHowto) but I dont know whether this is best to do, primarily because it seems to be doing something with xorg and also because all my mouse buttons work fine how they are now, just 2 of them have the wrong action set.

Any help would be great thanks!
Cheers, Jon.

---

### Post by argail1980 on 2009-09-02
hi,

funny that an update changes the buttons. anyway... could you post your ```
/etc/X11/xorg.conf
```

then: do you have imwheel installed?

type:
```
aptitude search imwheel
```

if there's an "i" at the start of the line it's installed, if there's a "p", it's not.

---

### Post by jon.mithe on 2009-09-02
Yeah, I honestly never knew how much I used it as well, I work in ubuntu and all throughout the day I have been subconsciously go to scroll across and it bumps my music right up and scare the... out of me. 

No I do not have imwheel installed, slightly reluctant to install it because my mouse buttons are all working, its just the actions / configuration has recently changed - and certainly they used to work perfectly before.  My Xorg below:

```
Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver	"fglrx"
EndSection

Section "ServerFlags"
	Option	"DontZap"	"False"
EndSection
```

I thought the ATI drivers had a strange relation ship with xorg, i.e. changing its not so good you have to do via the aticonfig tool.  Although, maybe this is just for the graphics sections.

I forgot to mention I'm running a simple/vanilla install of 9.04 desktop 64bit (uptaded from 8.10 fresh install (the update that cause the problem was not the 8.10->9.04 update, just a generic 9.04 update), 

```
unname -a:
Linux xxxxxxxxx 2.6.28-15-generic #49-Ubuntu SMP Tue Aug 18 19:25:34 UTC 2009 x86_64 GNU/Linux
```


Thanks, 
Jon

---

### Post by jon.mithe on 2009-09-02
hmm, getting the feeling its not possible to reassign button actions without mapping the button to an arbitrary keyboard shortcut (have no idea how linux is doing it in the first place).  Looked into things like xmodmap, but seem to be mapping / translating the buttons, i.e. turn left click into a right click.

Anybody know by anychance what the new sound / speaker app is? I want to try and destroy it and see if that fixes it :P (edit: hmmm, guess this will probably be part of gnome)

The one I'm talking about is if you adjust the volume by a keystroke or mouse, you get an overlay popup (like when you change tracks in amarok) in the top left corner.  Its black background with a silver volume slider.

Please help! :) I'm soon going to adopt the windows approach and just reformat + reinstall the whole os :/  Thought I'd never see the day :P

Thanks, 
Jon.

---

### Post by jon.mithe on 2009-09-02
rar, friend found a solution.

The app is the notifier app in unbuntu, and its just stealing mouse events.  Killing does not work I think it is because its a service, so just have to remove / disable it.   Found this on teh interwebs:

```
sudo mv /usr/share/dbus-1/services/org.freedesktop.Notifications.service /usr/share/dbus-1/services/org.freedesktop.Notifications.service.disabled 
```

Ah now I have horizontal scroll back :)

---

### Post by jimmy the fish on 2009-09-02
Winrar!

---

### Post by argail1980 on 2009-09-04
That kinda looks like a dangerous thing to do... what was that service for in the first place?

I had a look into the file and it doesn't look suspicious. Could you post the link where you found it, I'm curious

---

### Post by jon.mithe on 2009-09-04
Its the new notification app ('notify-osd') in 9.04 aimed at providing a framework for passive desktop notifications.

[http://packages.ubuntu.com/jaunty/notify-osd](http://packages.ubuntu.com/jaunty/notify-osd)

It is also a part of the growing bloat in ubuntu... :/

Disabling the service should be fine, but now I've just removed the notify-osd package from my system (synaptic, notify-osd -> remove!)

Once my friend said about the notify-osd process, and it just would not die when I killed it, a quick google search found

[http://www.killertechtips.com/2009/04/26/disable-notifications-in-ubuntu-904-jaunty-jackalope/](http://www.killertechtips.com/2009/04/26/disable-notifications-in-ubuntu-904-jaunty-jackalope/)

After digging around a bit I've read this app is causing a bit of frustration, especially with some users an endless torrent of wireless notifications.

---

