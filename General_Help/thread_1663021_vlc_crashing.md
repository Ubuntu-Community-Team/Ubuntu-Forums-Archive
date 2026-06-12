---
title: "vlc crashing"
date: 2011-01-09
forum: General Help
---

### Post by owners4life5 on 2011-01-09
hello,

i can't really give much info here, except that when i try to open a file with vlc (or totem for that matter) they crash. i use vlc mainly, though.

when i just open it by itself as a program, all is fine. but if i try to open up a file, it automatically crashes.

here is output from terminal, which all appears to be ok:

```
brian@brian-desktop:~$ vlc
VLC media player 1.0.6 Goldeneye
[0x8a0d668] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
brian@brian-desktop:~$ 
```

thanks in advance.

---

### Post by howefield on 2011-01-09
Rather than opening vlc itself via terminal. try opening the file via the terminal.

eg,

```
vlc name_of_file_which_causes_crash
```

---

### Post by owners4life5 on 2011-01-09
> **howefield said:**
> Rather than opening vlc itself via terminal. try opening the file via the terminal.

eg,

```
vlc name_of_file_which_causes_crash
```

i never even thought of that :/

but here is the output:

```
brian@brian-desktop:~$ vlc /media/"My Book"/"My Videos"/MOV03C.MOD
VLC media player 1.0.6 Goldeneye
[0x9d07668] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
[0xa06c620] a52 decoder: A/52 channels:2 samplerate:48000 bitrate:384000
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
[0xa0b26b8] pulse audio output: No. of Audio Channels: 2
[????????] x11 video output error: X11 request 132.19 failed with error code 11:
 BadAlloc (insufficient resources for operation)
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  132 (XVideo)
  Minor opcode of failed request:  19 ()
  Serial number of failed request:  103
  Current serial number in output stream:  104
brian@brian-desktop:~$ 
```

---

### Post by howefield on 2011-01-09
Sorry I can't help further, but I'd take the first error line 

```
x11 video output error: X11 request 132.19 failed with error code 11:
 BadAlloc (insufficient resources for operation)

```

and whack it into google, see what comes up and follow some of the links, eg.

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/374258](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/374258)

---

