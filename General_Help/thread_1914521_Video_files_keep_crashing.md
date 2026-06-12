---
title: "Video files keep crashing"
date: 2012-01-24
forum: General Help
---

### Post by gattz on 2012-01-24
I've been having a problem with video files lately, Ubuntu doesn't seem to want to play them properly. I always get lag and weird filter issues, and I'm not sure why. It seems to be a problem mostly with mkv files or HQ video files.

The biggest problem is that I get crashes all the time. I've tried multiple video players (VLC, SMplayer, Mplayer, Kaffeine, GNOME Player), and I'm always getting issues.

My last VLC crash log (same file):
```
kainx@kainx-HP-Compaq-6710b-RM406UT-ABA:~$ vlc
VLC media player 1.1.4 The Luggage (revision exported)
Blocked: call to unsetenv("DBUS_ACTIVATION_ADDRESS")
Blocked: call to unsetenv("DBUS_ACTIVATION_BUS_TYPE")
[0x9297914] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
Blocked: call to setlocale(6, "")
Blocked: call to sigaction(17, 0xb747e0d4, 0xb747e048)
Warning: call to signal(13, 0x1)
Warning: call to signal(13, 0x1)
Warning: call to srand(1326694982)
Warning: call to rand()
Blocked: call to setlocale(6, "")

(process:4467): Gtk-WARNING **: Locale not supported by C library.
	Using the fallback 'C' locale.
Warning: call to signal(13, 0x1)
Warning: call to signal(13, 0x1)
Blocked: call to setlocale(6, "")
 m_el[mi_level] == NULL
 arrrrrrrrrrrrrg Up cannot escape itself
 m_el[mi_level] == NULL
 arrrrrrrrrrrrrg Up cannot escape itself
Warning: call to rand()
[***] fontconfig: Selected font is not the requested one: 'DejaVu Sans' != 'Kimberley'
[0x95ebbf4] filesystem access error: failed to read (Input/output error)
[0xb7500b74] main input error: ES_OUT_SET_(GROUP_)PCR  is called too late (pts_delay increased to 300 ms)
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
number of reference frames exceeds max (probably corrupt input), discarding one
Warning: call to rand()
Warning: call to rand()
[0x95ebbf4] filesystem access error: failed to read (Input/output error)
```

---

### Post by carl4926 on 2012-01-24
You really shouldn't post info that shows you have been downloading pirated material.
You should PM a mod to edit it

Is your problem the same with .avi files
or only .mkv

---

### Post by gattz on 2012-01-24
Posted edited, added a VLC crash log and used code tags. Any help would be greatly appreciated because this is really getting on my nerves. I get that "frames exceeded" error when I try to convert mkv files to avi too.

---

### Post by ubudog on 2012-01-24
> **gattz said:**
> Posted edited, added a VLC crash log and used code tags.

Thank you.

---

### Post by carl4926 on 2012-01-24
> **gattz said:**
> Posted edited, added a VLC crash log and used code tags. Any help would be greatly appreciated because this is really getting on my nerves. I get that "frames exceeded" error when I try to convert mkv files to avi too.

Converting with what?
Handbrake works for me

Try this .mkv
[http://dl.dropbox.com/u/10573557/Ubuntu/ub_11.10_slideshow.mkv](http://dl.dropbox.com/u/10573557/Ubuntu/ub_11.10_slideshow.mkv)

Does it play

---

### Post by gattz on 2012-01-24
I'm trying to convert with Mencoder but I keep getting the "number of reference frames exceeds max" error. Yes, that video plays, I think the problem has to do with subtitles/audio/different codecs or something. Some video play without a hitch, others give me grief the entire time (pauses, crashes, lag, weird filter stuff).

---

### Post by SeijiSensei on 2012-01-24
Typical causes include a slow video card (older embedded Intel controllers in particular) or a slow CPU if your video card does not support hardware decoding of H.264-encoded material.  If you happen to have an NVIDIA 8xxx or later video card, are you using VDPAU?

How about some specs on your computer and video card?

Older hardware just can't cut it when trying to play H.264-encoded 720p or 1080p videos.

---

### Post by gattz on 2012-01-24
2 GB RAM
Intel Core 2 Duo CPU T8100 @2.10GHz

Seems this laptop uses an integrated graphics controller.

---

