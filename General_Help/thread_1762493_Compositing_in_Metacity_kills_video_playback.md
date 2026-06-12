---
title: "Compositing in Metacity kills video playback"
date: 2011-05-19
forum: General Help
---

### Post by DirtyDawg on 2011-05-19
guys when i enable metacitys compositing feature so i can run docky, any videos i play i cant see them, they load and the sound works but just a black screen, any ideas?

Using Totem for video playing
Using Ubuntu 10.10 as OS
Enabling compositing through a check box in UbuntuTweak
No gfx card, just onboard one.

Any help would be appreciated as i am lost  :confused:

---

### Post by TeoBigusGeekus on 2011-05-19
Have you tried with another player? (vlc, mplayer, etc.)
Also, open totem with the command line
```
totem
```
and post us any error messages you get while playing a video.

---

### Post by DirtyDawg on 2011-05-19
vlc
VLC media player 1.1.4 The Luggage (revision exported)
Blocked: call to unsetenv("DBUS_ACTIVATION_ADDRESS")
Blocked: call to unsetenv("DBUS_ACTIVATION_BUS_TYPE")
[0x83ef914] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
Blocked: call to setlocale(6, "")
Blocked: call to sigaction(17, 0xb74620d4, 0xb7462048)
Warning: call to signal(13, 0x1)
Warning: call to signal(13, 0x1)
Warning: call to srand(1306497149)
Warning: call to rand()
Blocked: call to setlocale(6, "")

(process:5771): Gtk-WARNING **: Locale not supported by C library.
	Using the fallback 'C' locale.
Warning: call to signal(13, 0x1)
Warning: call to signal(13, 0x1)
Blocked: call to setlocale(6, "")
Blocked: call to setenv("_PX_CONFIG_ORDER", "", 1)
Blocked: call to setenv("_PX_CONFIG_ORDER", "", 1)

Output ^ from running VLC from terminal, i dont get any error messages just
a black screen and sound, i noticed tho if i move the window by clicking
on the title bar and dragging the vlc window then the video appears for a 
second, on and off ?

---

