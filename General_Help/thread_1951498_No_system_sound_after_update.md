---
title: "No system sound after update"
date: 2012-04-02
forum: General Help
---

### Post by Chip88 on 2012-04-02
Hey there!

Looked here in the forum for anything useful and searched also in Google, but didn't find anything.

After an update from KDE 4.7.4 to KDE 4.8.1 I realized, that all system sounds for turned off suddenly and didn't work anymore.

But all sound settings were set correct and phonon was configured also the right way. There were no problem listening to music or watching movies.


Today I saw, that the paths to the corresponded sound files were incorrect.

In *system settings &#8594; Notifications &#8594; KDE - Desktop and system settings* and *system settings &#8594; Notifications &#8594; KDE - Energy settings* the paths to the sound files were wrong.

Instead of the needed whole path */usr/share/sounds/NAME_OF_THE_SOUNDFILE.ogg* there was just the *sounds/NAME_OF_THE_SOUNDFILE.ogg*.

I changed everything manual now, but I wanted to know, why the paths were changed at all and if there is a possibility to change the paths automatically, i. e. with a command?!

Have a nice evening and thanks in advance for your help!

Regards,
Chipy

---

