---
title: "Problems after dist-upgrade"
date: 2009-07-02
forum: General Help
---

### Post by guedesav on 2009-07-02
I've just dist-upgraded my Ubuntu to Intrepid Ibex, and now I'm experiencing a few little annoying problems...

1- My mouse doesn't work on Xorg, unless I start dbus/hald. And, before anyone asks, dbus and HAL were deactivated due to another annoying problem: hal, for some unknown reason, always managed to disconfigure my keyboard to evdev, messing up with the whole keymap.

2- And talking about keyboards, since the upgrade my keyboard can't accentuate anymore. I can manually set xmodmap, but, really, there's no reason for this not to be made automatically anymore...

3- Also, now gnome-settings-daemon doesn't work, except in GNOME. I usually(actually, almost always, save for two exceptions) use Fluxbox, and this is what I get:

```
# gnome-settings-daemon --no-daemon

** (gnome-settings-daemon:15670): WARNING **: Couldn't connect to session bus: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

** (gnome-settings-daemon:15670): WARNING **: Could not get a connection to the bus
```

and then any other gnome configuration program will give me tons of error messages I never had before.

I'm trying to understand what's going on, since I never had such problems in Hardy, and now Intrepid is making my life actually *harder*. Not to mention the kernel almost didn't boot. But now the system is upgraded already, so I guess it's up to me to fix it, and I'd appreciate any help.

So, thanks in advance, good morning/afternoon/night and good luck.

---

### Post by steveneddy on 2009-07-02
So you were on Gutsy and upgraded to Ibex?

From what I can remember it is best not to dist-upgrade - do a total reinstall and backup /home beforehand to reinstall afterwards.

---

### Post by guedesav on 2009-07-02
That's very sad to hear. I had to manually install the drivers for my wireless card, webcam and tablet, and it was not easy. That's basically the reason I do not wish to reinstall this system by any costs.

...but, now that you mentioned it, what's dist-upgrade meant for, then? I did and upgrade before, BTW, and it didn't do much better either...

---

### Post by guedesav on 2009-07-03
Okay, now I went all the way and reinstalled Ubuntu with 8.10. Everything's good so far, except TWO things...

1- My monitor's resolutions is ridiculously small now. It only lets me set it to 640x480 or 800x600. xrandr can't change it beyond, the GNOME configuration tool also doesn't, and xserver-xorg reconfiguration tool is with that new "feature" that only configures the keyboard...

2- When running KDE applications by other users(root, for example) I get strange error messages saying it can't find D-Bus, except dbus is active, so I don't get it.

That being said, I find it very strange that an upgrade would make my life *harder*, instead of better.

EDIT: Also, I just found out my keymap came up without the special fuctions(volume up/down, mute, etc)...

And number 4- Firefox and a few other aplications are displaying a strange "problems while loading settings" message box. I think this has to do with me not using GNOME and thus not activating the gnome-settings-daemon. But that's very strange, cause I had no problem in version 7.10... another of Ubuntu's lovely new "features"? :)

---

### Post by guedesav on 2009-07-03
Good thing I had one huge backup of my root directories sitting around, so I could copy-paste the monitor sections from my old xorg.conf to this new one. Good thing, cause there was no other way to configure my video since "dpkg-reconfigure xserver-xorg" was set to only configure the keyboard!

Now, really, I understand Xorg is now good and efficient, and can probably detect most of the comercial video cards around but... why taking away the configurations completely?! Really, you should always err for the safe side, and this is one thing I can say Ubuntu screwed up HARD on.

...And back to the usual stuff, please, any help on the D-bus and settings problem is quite appreciated. And no, switching to GNOME is not an option I'm willing to take...

---

