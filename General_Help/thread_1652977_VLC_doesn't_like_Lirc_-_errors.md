---
title: "VLC doesn't like Lirc - errors"
date: 2010-12-26
forum: General Help
---

### Post by martygeek on 2010-12-26
I just recenyly switched over from Fedora to Ubuntu. I am very pleased with Ubuntu with the exception of the VLC and Lirc operation.

I have Lirc working and can control RythmBox well with my remote.  When I try to do the same with VLC I get nothing.  I get errors when trying to run VLC with the lirc interface :
[INDENT] vlc -I lirc movie.avi 
VLC media player 1.1.4 The Luggage (revision exported)
Remote control interface initialized. Type `help' for help.
Blocked: call to unsetenv("DBUS_ACTIVATION_ADDRESS")
Blocked: call to unsetenv("DBUS_ACTIVATION_BUS_TYPE")
[0x8c0a224] lirc interface error: lirc initialisation failed
[0x8c0a224] main interface error: no suitable interface module
[0x8b5b914] main libvlc error: interface "default" initialization failed
status change: ( stop state: 0 )
status change: ( quit )
[/INDENT]If I try the extraintf, I can similar errors, but then locaization fails (I use korean fonts for subtitles)

[INDENT]marty@koreaboy:~$ vlc --extraintf lirc Desktop/Movies/5.0-Eat\ Pray\ Love.2010.R5.LiNE.Xvid\ \{1337x\}-Noir/Eat\ Pray\ Love.2010.R5.LiNE.Xvid\ \{1337x\}-Noir.avi 
VLC media player 1.1.4 The Luggage (revision exported)
[0x9423e44] lirc interface error: lirc initialisation failed
[0x9423e44] main interface error: no suitable interface module
Blocked: call to unsetenv("DBUS_ACTIVATION_ADDRESS")
Blocked: call to unsetenv("DBUS_ACTIVATION_BUS_TYPE")
[0x938c914] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
Blocked: call to setlocale(6, "")
Blocked: call to sigaction(17, 0xb5e6b0d4, 0xb5e6b048)
Warning: call to signal(13, 0x1)
Warning: call to signal(13, 0x1)
Warning: call to srand(1293739734)
Warning: call to rand()
Blocked: call to setlocale(6, "")

(process:30661): Gtk-WARNING **: Locale not supported by C library.
    Using the fallback 'C' locale.
Warning: call to signal(13, 0x1)
Warning: call to signal(13, 0x1)
Blocked: call to setlocale(6, "")
[/INDENT]I can run it without errors if I use vlc -I rc, but the remote still doesn't work.

Any ideas what I should be doing differently?

Thanks,
Marty

---

