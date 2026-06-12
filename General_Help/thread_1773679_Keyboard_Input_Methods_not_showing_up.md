---
title: "Keyboard Input Methods not showing up"
date: 2011-06-02
forum: General Help
---

### Post by thameera on 2011-06-02
I switched to pure LXDE desktop in my Ubuntu and now my Keyboard Input Methods dialog doesn't show up. When I click on the menu item nothing happens. The Preferences menu item in the keyboard icon in the panel doesn't work either.
Please help, coz I badly need to switch languages while typing.

---

### Post by johngreth on 2011-06-02
try running
```
ibus-daemon
```
in the terminal. This should manually start the process. Then try opening the preferences.

---

### Post by thameera on 2011-06-02
> **johngreth said:**
> try running
```
ibus-daemon
```
in the terminal. This should manually start the process. Then try opening the preferences.
I tried that, but it says 'current session already have an ibus-daemon' :S

---

### Post by kerry_s on 2011-06-02
so what does it say when you type "lxkeymap" in terminal?

---

### Post by johngreth on 2011-06-02
Try running Administration -> Language Support, and applying System-Wide Support. iBus gave me a message that it needed to be configured when I ran the command.

---

### Post by kerry_s on 2011-06-02
> **johngreth said:**
> Try running Administration -> Language Support, and applying System-Wide Support. iBus gave me a message that it needed to be configured when I ran the command.

have you ever used lxde?
@thameera, "system tools" instead of "Administration" under lxde menu

@thameera, if you intend to use gnome stuff in lxde, you'll need to have the proper gnome startup apps in lxde startup. check preferences-> desktop session settings.

are menu looks like this.

---

### Post by thameera on 2011-06-03
When I type lxkeymap, the lxkeymap window shows up.
I've already added iBus-daemon to the startup applications. It loads at startup, the problem is I can't access its Preferences. Do I need to start any other service at startup for this?

---

### Post by whatthefunk on 2011-06-03
I run Lubuntu and had similar problems.  Im not on my home machine now, but I think that I added the Keyboard Input Methods icon to the tool bar on the bottom near the clock and then could access everything from there.  i cant remember though.  When I get home tonight I can take a look at it.

---

### Post by kerry_s on 2011-06-03
yeah, like he said theres a panel applet you add to switch.

ps: i don't have no ibus-daemon, so doubt it's even needed. you might be having problems because you added lxde on top of ubuntu gnome, you may want to consider a straight lubuntu install, much faster & cleaner app wise.
[http://lubuntu.net/](http://lubuntu.net/)

---

### Post by thameera on 2011-06-03
Any idea how to add a language to that Keyboard Layout Switcher applet? Mine has only the US layout.

---

### Post by kerry_s on 2011-06-03
> **thameera said:**
> Any idea how to add a language to that Keyboard Layout Switcher applet? Mine has only the US layout.

type-> gksudo leafpad /etc/default/keyboard
add your languages to:
XKBLAYOUT="us"


i think theres also a command that does the same thing, but i forget, hit google.

---

### Post by whatthefunk on 2011-06-04
To add a language: Go to Preferences > Language Support This will open the Language and Text window Click on "Install/Remove Languages" and select the language you want to add.  It will automatically install the language files and should enable the Keyboard Input Methods window.  Go to Preferences > Keyboard Input Methods When you do this, a window will pop up asking if you want to start iBus.  Click yes.  Then you will see the iBus Preferences window where you can select the input method that you want and do things like assign a hotkey.  The iBus icon should appear down by the clock now.  After a reboot, you should be able to go to Preferences > Desktop Session Settings and make iBus start automatically on boot.

---

### Post by thameera on 2011-06-04
> **whatthefunk said:**
> Go to Preferences > Keyboard Input Methods 

The problem I'm having is that when I click on Keyboard Input Methods nothing happens. No window shows up. :/

---

### Post by whatthefunk on 2011-06-04
> **thameera said:**
> The problem I'm having is that when I click on Keyboard Input Methods nothing happens. No window shows up. :/

 What language are you trying to install?  Do you see the small box with an i in it near the clock?

---

### Post by jastonas on 2011-10-03
How I would like to see this fixed!

---

### Post by poikiloid on 2013-04-09
the problem is some missing dependencies in the ibus package for lubuntu, as described here: [https://bugs.launchpad.net/ubuntu/+source/ibus/+bug/1041933/comments/4](https://bugs.launchpad.net/ubuntu/+source/ibus/+bug/1041933/comments/4)
without them, you do not get the "i" icon in the panel. you DO NOT get this icon via the Keyboard Layout Handler applet, that is for switching the ACTUAL keyboard type, not for input methods.

use synaptic or whatever, and make sure you have all these installed, then, log out and back in:

libappindicator1
python-appindicator
python-gconf
python-glade2
python-pexpect

---

