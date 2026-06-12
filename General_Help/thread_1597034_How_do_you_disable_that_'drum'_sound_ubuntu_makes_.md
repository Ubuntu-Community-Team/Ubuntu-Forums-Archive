---
title: "How do you disable that 'drum' sound ubuntu makes upon start up?"
date: 2010-10-14
forum: General Help
---

### Post by dogdo on 2010-10-14
I want to get rid of this sound at startup but keep all other sounds like when watching a video online or music...

---

### Post by Hoopz on 2010-10-14
system>preferences>sound

---

### Post by Hoopz on 2010-10-14
oh wait I see what you're talking about that one that plays just as the login screen comes up

---

### Post by LucidForm on 2010-10-14
System -> Administration -> Login Screen

---

### Post by orangemoose on 2010-10-18
Two issues being discussed here: 1. Beautiful Ubuntu sound. 2. Sharp drum sound.

#1 can be set using the GUI.

Go to System -> Preferences -> Starup Applications
Look for &#8220;GNOME Login Sound&#8221; in the list. If you don&#8217;t want to hear anything at startup, uncheck this box.


#2 has no GUI access. Workaround provided by Barry Warsaw.
==============
WORKAROUNDS
==============
NOTE: These workarounds disable the "system ready" sound (the drums). They will not disable the "successful login" and "logout" sounds. Go to Settings -> Sounds and set the sound theme to "no sounds" to disable these.

1) Disable all sounds for the login screen via gconf
$ sudo su gdm -c "gconftool-2 --set /desktop/gnome/sound/event_sounds --type bool false"

-OR-

2) Rename the system-ready.ogg sound file
$ sudo mv -v /usr/share/sounds/ubuntu/stereo/system-ready.ogg{,.disabled}

==============
BUG
==============
When you log into Karmic using a Gnome session, you get a drum sound. There are many situations where you need a silent boot process, but it appears that this is impossible under Karmic.

In Jaunty and previous, you could configure gdm to log you in silently. This configuration has been removed from Karmic. Even opening Sound Preferences and choosing "No sounds" for "Sound theme" or disabling window and button sounds does not prevent the login sound from occurring.

Users must have the ability to login silently.

---

