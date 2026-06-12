---
title: "launch Chrome in incognito mode by default from the Unity Launcher"
date: 2012-05-19
forum: General Help
---

### Post by hopefulkayaker on 2012-05-19
Is there a way in 12.04 to launch Chrome in incognito mode by default, simply by left-clicking on its Launcher icon?

I'm aware of the -incognito flag, and I managed to find the way to do it via Gnome's Main Menu, but well, Unity's still pretty crappy when it comes to things like this I'm sorry to say. :-/

---

### Post by 2F4U on 2012-05-19
Maybe these two links are helpful:

[http://maketecheasier.com/8-really-useful-ubuntu-unity-quicklists/2011/05/07](http://maketecheasier.com/8-really-useful-ubuntu-unity-quicklists/2011/05/07)
[http://notes-cs.blogspot.de/2012/02/set-chrome-incognito-mode-as-default-in.html](http://notes-cs.blogspot.de/2012/02/set-chrome-incognito-mode-as-default-in.html)

---

### Post by stinkeye on 2012-05-19
```
gksudo gedit /usr/share/applications/google-chrome.desktop
```

and change the exec line (line 108 on mine) to...
```
Exec=/opt/google/chrome/google-chrome --incognito
```

---

### Post by mc4man on 2012-05-19
Just to add to stinkeye's post which is the way to do. I'd leave the %U so new Exec= would be
```
Exec=/opt/google/chrome/google-chrome --incognito %U
```

And if you already had chrome pinned you may want to unpin, then add back (may not matter - if the existing doesn't now open in incognito then do

---

### Post by stinkeye on 2012-05-19
...and if you don't want the change to affect other users, copy the .desktop file instead of
editing it as root.
eg
```
cp /usr/share/applications/google-chrome.desktop ~/.local/share/applications
```

and then edit the copied file...
```
gedit ~/.local/share/applications/google-chrome.desktop
```

May need to log out/in.

---

### Post by hopefulkayaker on 2012-05-19
Thank you! I've got it working now.

---

