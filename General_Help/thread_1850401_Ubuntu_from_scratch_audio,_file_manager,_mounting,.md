---
title: "Ubuntu from scratch: audio, file manager, mounting, shutdown"
date: 2011-09-26
forum: General Help
---

### Post by J V on 2011-09-26
I'm installing ubuntu cli version, with openbox on it from scratch. I intend to have a lightweight system with all the benefits of moderately well-kept packages.

So far I have openbox running (startx command ftw :D) and I installed the latest nvidia drivers (Work like a charm in wine)

I want to get hardware/low level software problems out of the way so that I can focus on preferences later.

Things that don't work:

[LIST]
[*]**Audio** - Much as I hate it, pulseaudio is becoming the norm, and it's wine compatability is approaching decency. Pulseaudio package is installed but "ps aux | grep pulse" shows it's not running. FIXED (Installed pavucontrol etc from pre8.x guide) BROKEN since I added xinitrc
[*]But I would still like to be able to change pulseaudio volume with multimedia keys without resorting to alsa mixers
[*]**composite manager** for screencapture, not fancy effects. But I don't know which to use (xcompmgr is the only option but it screws with firefox so that's a no-go)
[*]I need a **file manager** that can one-click mount a drive. Xfe doesn't do it and I don't weather that's normal or it's because I need a FIXED fstab of course
[*]**login manager** - Or do I need this? I was never certain what it did other than offer a GUI. On a related note, I want to be able to shutdown without typing in my password. I assume this is also a login manager specialty?
[*]**Xorg kill shortcut** - In gnome there's some obscure gconf key that lets you kill xorg with ctrl+alt+bs but this isn't gnome so how do I make it work? used xinitrc
[*]**Conky tutorial** anyone?
[/LIST]

---

