---
title: "Can't boot into Kubuntu..."
date: 2009-11-05
forum: General Help
---

### Post by PaperPhantom on 2009-11-05
I reinstalled Kubuntu 9.10 about an hour ago (I've been having these constant issues, and just now decide to ask for help), and something is already screwed up again.

There are several issues I have right now, but the important ones first.

As mentioned in the topic title, I cannot boot. I could before, and now I can't.

I mean, when I was trying to "Enable" desktop effects, the entire system froze. Sort of. I could still move the mouse/cursor, but that's it.

When I tried to boot back into Kubuntu, I would get as far as the login screen, but after entering my info, when that splash screen comes up which shows the disk, and other stuff, only the disk "loads", after that, it freezes all over again.

I suspect this is because of the desktop effects thing, so I was wondering, is there anyway to undo that setting, without reinstalling it all over again?

---

### Post by soapBAR2 on 2009-11-05
You can reset your settings by re/moving your KDE folder. Just

```
sudo mv ~/.kde ~/.kde-inert
```

or

```
sudo rm ~/.kde
```

You can get into a terminal by pressing Ctrl+Alt+F1 anytime after it's booted.


Update: Or, if you just want to turn off the effects, the settings are in ~/.kde/share/config/kwinrc. Just set all the plugins to false.

---

### Post by ashishmalik10 on 2009-11-05
> I was trying to "Enable" desktop effects, the entire system froze

Login into your gnome account. Go to System -> Preferences -> Appearance -> Visual Effects.

If you have custom effects enabled then go to preferences and deselect the "Enable Extra Animations" checkbox.
Otherwise, select NONE in visual effects and see if it works. 

If you  can't login into genome then login in "Genome Failsafe".
Hope it might be of some help.   ):P

---

### Post by PaperPhantom on 2009-11-05
> **soapBAR2 said:**
> You can reset your settings by re/moving your KDE folder. Just

```
sudo mv ~/.kde ~/.kde-inert
```or

```
sudo rm ~/.kde
```You can get into a terminal by pressing Ctrl+Alt+F1 anytime after it's booted.


Update: Or, if you just want to turn off the effects, the settings are in ~/.kde/share/config/kwinrc. Just set all the plugins to false.

Thanks, that did the trick.

> **ashishmalik10 said:**
> Login into your gnome account. Go to System -> Preferences -> Appearance -> Visual Effects.

If you have custom effects enabled then go to preferences and deselect the "Enable Extra Animations" checkbox.
Otherwise, select NONE in visual effects and see if it works. 

If you  can't login into genome then login in "Genome Failsafe".
Hope it might be of some help.   ):P

While I really do appreciate the help, I don't have Gnome. Thanks anyway. =)



I do have another problem. Sometimes when I boot, the entire computer freezes. This happens after selecting an operating system, and after the Kubuntu splash page. Immediately afterwards, actually. So I don't even make it to the login, and all I see is a black screen, with nothing on it.

While I am usually (Eventually...) able to boot, it's a real hassle, because sometimes it takes as many as 5-6 tries before I actually do get to the login screen.

Any ideas?

---

### Post by PaperPhantom on 2009-11-05
Anyone?

---

### Post by PaperPhantom on 2009-11-05
bump

---

