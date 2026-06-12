---
title: "Can't use firefox and music at the same time"
date: 2010-01-31
forum: General Help
---

### Post by letmekilluplz on 2010-01-31
I can't play Rhythmbox and Firefox at the same time. The program that starts first is the one that will play sound. I read that is you install libflashsupport and switch to Pulseaudio it will work. I tried to install the package which then pointed me to another package which I installed but I can't find an option under System> Preferences> Sound to switch. Any help?

---

### Post by towheedm on 2010-01-31
If you want to play multiple streams at the same time you need to have Pulseaudio installed.  Check out the following thread:

[http://ubuntuforums.org/showthread.php?p=4928900&highlight=partition+size](http://ubuntuforums.org/showthread.php?p=4928900&highlight=partition+size)

Hope this helps.

---

### Post by letmekilluplz on 2010-01-31
Followed the guide and now I can use rythmbox and Firefox at the same time but I can't get the MMORPG I play to play sound at the same time as Rythmbox. Not sure if its a browser a game problem now but thanks.

---

### Post by towheedm on 2010-02-01
I'm not a gamer myself so I'm not familiar with those.  You may want to check the Playback tab in pavucontrol (PA Volume Control) and check whether both Rhythmbox and the game streams are listed.  If they are, see whether the game somehow mutes the Rhythmbox stream or vice-versa.  This might give you a clue as to what is happening.

I myself have had some really weird muting problems with pulseaudio which ended after I completely uninstalled and then re-installed it.

---

