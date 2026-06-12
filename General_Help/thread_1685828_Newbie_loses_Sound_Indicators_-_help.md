---
title: "Newbie loses Sound Indicators - help"
date: 2011-02-11
forum: General Help
---

### Post by Quarkrad on 2011-02-11
Running 10.10  I was having trouble with Clementine audio player - keep coming up with something like error - streaming cannot connect.   Anyway, rather than jumping to this forum I googled around and considered(?) opinion seemed to be to remove pulseaudio.  I have done this and install gnome audio and I have corrected my original problem.  I have sound - no problem.  I can play audio through Clementine and there are no errors.  I get sound if I hover the cursor over an audio file in nautilus.  Absolutely no sound problems.  My issue is I have no control - there is no sound icon in the top panel and nothing no Sound option in System, Preferences.  I have tried adding Indicator Applet but all that does is give me duplicate Battery and Mail icons.  Help.

---

### Post by Quarkrad on 2011-02-11
This got my volume control back - although basic

[http://www.jeffsplace.net/node/12](http://www.jeffsplace.net/node/12)

---

### Post by Quarkrad on 2011-02-11
Errr back to where I started - rebooted and volume icon is no longer in top panel.  Help

---

### Post by Quarkrad on 2011-02-11
This may help - just tried **gconftool --recursive-unset /apps/panel && killall gnome-panel**.  Panel came back but still no Volume control.

---

