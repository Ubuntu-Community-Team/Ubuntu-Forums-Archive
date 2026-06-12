---
title: "[iBus] Pinyin Input Method, no character box"
date: 2011-06-12
forum: General Help
---

### Post by UncleJack0 on 2011-06-12
Hi,

PLATFORM:
Ubuntu 10.10

PROBLEM:
iBus doesn't seem to work properly. I can enter Chinese characters via pinyin but the characters choice box isn't there. It's typing by blind faith.

RECENT CHANGES:
1. I uninstalled Docky and installed Cairo-Dock

2. I tried to remove gnome-panel using

```
gnome-session remove gnome-panel
```

which brought about a havoc in the Terminal; a waterfall of text I didn't read (mostly error messages). I force-quitted the Terminal, logged off and in.

3. I "uninstalled" the gnome-panel using this code, entered in Terminal:

```
gconftool-2 --type=list --list-type=string --set /desktop/gnome/session/required_components_list '[windowmanager,filemanager]'
```

The code is supposedly used to remove the necessity of having that panel via gconf.

3. I installed several Cairo-Dock applets.

MORE INFO:
I cannot seem to remember when it was still working properly, so I don't know why it happened. I think it might have something to do with the gnome-panel, tho.

Thanks for any help you might bring to this forum :)

---

### Post by UncleJack0 on 2011-06-12
Ah, it seems that the problem can be solved by reinstalling the iBus package. First, exit any ibus-daemon you have, then do

```
sudo add-apt-repository ppa:shawn-p-huang/ppa 
sudo apt-get update 
sudo apt-get install ibus-gtk ibus-qt4 ibus-pinyin ibus-pinyin-db-open-phrase
```

Then it should work.

---

