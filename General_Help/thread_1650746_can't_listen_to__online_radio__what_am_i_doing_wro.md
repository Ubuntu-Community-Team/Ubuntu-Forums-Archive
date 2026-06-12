---
title: "can't listen to  online radio  what am i doing wrong???"
date: 2010-12-22
forum: General Help
---

### Post by 5PUTN|K on 2010-12-22
Im trying to listen to  [this]("http://www.radyoodtu.com.tr/canliyayin.htm") radio station using firefox but i can't. It has two versions the one on the left is for windows media player and the other one is something like the bbc radio iplayer i could listen to the iplayer version yesterday but something happened and now i just can't. Anyways i tried playing it using vlc 
```
vlc http://www.radyoodtu.com.tr/iplayer/index.asp
```
but it seems even vlc cant play it heres the output
```
deniz@deniz-laptop:~$ vlc http://www.radyoodtu.com.tr/iplayer/index.asp
VLC media player 1.1.4 The Luggage (revision exported)
Blocked: call to unsetenv("DBUS_ACTIVATION_ADDRESS")
Blocked: call to unsetenv("DBUS_ACTIVATION_BUS_TYPE")
[0x25c5150] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
Blocked: call to setlocale(6, "")
Blocked: call to sigaction(17, 0x7f74bc15bb20, 0x7f74bc15ba80)
Warning: call to signal(13, 0x1)
Warning: call to signal(13, 0x1)
Warning: call to srand(1292950581)
Warning: call to rand()
Blocked: call to setlocale(6, "")

(process:4662): Gtk-WARNING **: Locale not supported by C library.
    Using the fallback 'C' locale.
Warning: call to signal(13, 0x1)
Warning: call to signal(13, 0x1)
Blocked: call to setlocale(6, "")
Blocked: call to setenv("_PX_CONFIG_ORDER", "", 1)

```

what am i doing wrong  and how do i fix it ???:confused:

---

### Post by 5PUTN|K on 2010-12-22
turns out i was using the wrong link..... sorry my bad now when i use  this command
```
cvlc mms://144.122.56.15/RadioODTU
```it just works like magic :lol:

---

