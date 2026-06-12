---
title: "Audio Overload doesn't play from menu."
date: 2011-10-25
forum: General Help
---

### Post by Infinite Indefinite on 2011-10-25
(Note: the following relates to an old version of Ubuntu - 6.10 to be precise.)

After placing Audio Overload in the Applications Menu, I found that though it loaded, it wouldn't play any files.

The error message stated that /dev/dsp/ was busy.  Apparently, the menu system sound prompted Audio Overload to determine that the sound device was permanently occupied.

A solution is to have Audio Overload start three seconds after it is selected.  The very simple attached script does that.

Simply place it in the PATH directory (ex: /usr/bin/ or /usr/local/bin/), and render it executable for all users:

```
sudo chmod -c a+rx AO.sh
```

Then use AO.sh as the command for Audio Overload in the Applications Menu.

(*I've also attached an icon for Audio Overload*.)

---

