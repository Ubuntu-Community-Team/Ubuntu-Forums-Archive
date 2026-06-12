---
title: "Shared libraries broken in 10.10 recently?"
date: 2011-05-02
forum: General Help
---

### Post by anlag on 2011-05-02
As of a few days ago, I believe Friday, there are certain applications that used to work fine that now produce error messages and won't run. Notably vlc does this:

> VLC media player 1.1.4 The Luggage (revision exported)
Blocked: call to unsetenv("DBUS_ACTIVATION_ADDRESS")
Blocked: call to unsetenv("DBUS_ACTIVATION_BUS_TYPE")
[0x923d914] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
[0x92ee3ec] main interface error: possibly corrupt module cache
[0x92fca54] main generic error: possibly corrupt module cache
[0x92ee3ec] skins2 interface error: no suitable dialogs provider found (hint: compile the qt4 plugin, and make sure it is loaded properly)
[0x92ee3ec] skins2 interface error: cannot instanciate qt4 dialogs provider


...and evince does this:

> evince: error while loading shared libraries: libexpat.so.1: failed to map segment from shared object: Permission denied

However while vlc is broken, cvlc (gui-free version) works, and so for instance do totem and mplayer for video, and acroread for pdfs. 

Did some recent update break some libraries, or could I have done something to cause this? I can't think of anything in particular that I did, but... who knows.

Oh, the error message for vlc suggests something about the qt4 plugin, I've checked that both my libqt4-gui and libqtgui4 (not sure of the difference) are latest version, if that matters. There are tons of other packages relating to qt4, I'm not sure if I should check or even reinstall any others.

Also I suppose I will upgrade to 11.04 soon enough, but for one not sure that will fix it and also would like to have a fully working machine until I have the opportunity to do the upgrade.

Thanks.

---

### Post by anlag on 2011-05-07
OK so I decided it wasn't worth fighting with 10.10 when 11.04 is out, so I upgraded and while I did so also made the leap to 64-bit, at long last. Now, I'm not sure this is even a related error, but after having VLC for for a few days I'm now getting the following when I try to start it from terminal:

> anlag@casper:~$ vlc
VLC media player 1.1.9 The Luggage (revision exported)
Blocked: call to unsetenv("DBUS_ACTIVATION_ADDRESS")
Blocked: call to unsetenv("DBUS_ACTIVATION_BUS_TYPE")
[0x1c13120] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
[0x1d09790] main interface error: possibly corrupt module cache
Segmentation fault


However, if I start it using the Unity launcher, VLC starts up fine. The version given in the About menu entry of the launcher-started VLC is the same as the crashing one I get in the terminal.

Incidentally I'm also having trouble with other video players, namely mplayer/smplayer, so I suppose I can't entirely rule out hardware issues with my NVIDIA card or such, but really if anyone can think of any other explanation... much obliged.

---

