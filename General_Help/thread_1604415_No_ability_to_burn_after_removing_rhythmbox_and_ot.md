---
title: "No ability to burn after removing rhythmbox and other oddities."
date: 2010-10-24
forum: General Help
---

### Post by there.is.only.xul on 2010-10-24
For some reason or another, after I removed rhythmbox, it seems I lost the ability to burn OS ISOs and not be able to use the disk burning software.

Is this just the operating system malfunctioning after close to a month's use on USB? A minimum space requirement before burning? This might not be a problem with Rhythmbox, but due to Ubuntu's tight integration with it, I am making removal of it suspect to what's going on.

Another oddity, the new interface that keeps songs updated in the volume control panel is nearly worthless using Amarok. I thought passing system notifications using the system notifier (libnotify) instead of using the stand-alone notifications would work, but it doesn't have the same feel as when running in Rhythmbox, where even before 10.10 and the volume control additions for playback and current song, I could at least see what's playing in a stream. Is there a special file that makes this stuff work?

I know it isn't gstreamer because music files still play on hover. Is this an unresolvable problem with Amarok, or is there a script I can add to make the notifications in-stream work like in Rhythmbox?

---

### Post by akand074 on 2010-10-24
Not sure about the notifications thing, I'm sure there is a way. I have yet to install Maverick on my desktop so I can look around but about your ISO thing, perhaps you uninstalled brasero? That is Ubuntu's default ISO burning software. Just reinstall it:

```
sudo apt-get install brasero
```

You could also just open up the software manager I'm sure there is other ISO burning software in there as well, perhaps one you might like better. Hope this helps at all.

---

