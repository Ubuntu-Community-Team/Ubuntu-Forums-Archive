---
title: "Weird Freezes After Messing Around With (and Then Removing) Compiz"
date: 2011-05-12
forum: General Help
---

### Post by dniMretsaM on 2011-05-12
[S]Ok, so I installed Compiz on Kubuntu 11.04 trying to do something which didn't work (I found out that it's super easy to do in KDE anyway). So I put Kwin back as the default window manager and then uninstalled Compiz. I rebooted my system as was suggested when I reset Kwin as the window manager, and when it booted back up, it froze. I worked for a few seconds and then everything except the Eyes widget and the mouse stopped doing anything. So I rebooted and it didn't do anything at all (no eyes even). I figured I'd just reinstall Kwin quessing that something got messed up with it when I was messing with Compiz. So I booted into recovery mode -> command line and ran
```
apt-get remove kwin
```It gave me some error about not being able to remove virtual packages or something like that. I'm out of ideas so any suggestions?[/S]

It seems to have resolved itself.

---

