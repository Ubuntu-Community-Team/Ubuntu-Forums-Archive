---
title: "problem with Trash: it starts vlc"
date: 2011-05-16
forum: General Help
---

### Post by ubunlilluz on 2011-05-16
hi,
since i passed to 11.04 i'm having problem with the trash. When i try to open it clicking over its icon the pc stops (only mouse cursor works) for about one minute then Vlc start running.
I've also a second internal hd that i use for the storage that normally is unmounted, but when i mount it (by clicking in the menu resource), it also run vlc.
What can i do for solving
thanks

---

### Post by mc4man on 2011-05-16
Try opening home folder (view > show hidden files) > .local/share/applications and deleting mimeapps.list
(you'll lose any file associations previously set, no big deal, they'll be reset upon use and a new mimeapps.list created

Or open it up and at the very top, _if not there,_ create a new section and add a line - 
```
[Default Applications]
inode/directory=nautilus-folder-handler.desktop

```

I'd just delete it and let a new one be created - natty uses a slightly different format where there is a [Default Applications] section and an [Added Associations] section

Ex. on a fairly new install this is the current one here
> [Default Applications]
x-content/audio-cdda=vlc-cd.desktop
inode/directory=nautilus-folder-handler.desktop
x-content/video-dvd=totem-xine.desktop
x-content/audio-player=vlc.desktop
x-content/image-dcf=shotwell.desktop
x-scheme-handler/mailto=userapp-Evolution-S779UV.desktop
application/x-shellscript=gedit.desktop
text/plain=gedit.desktop
audio/flac=audacious2.desktop

[Added Associations]
x-content/audio-cdda=vlc-cd.desktop;audacious-cd.desktop;
inode/directory=vlc.desktop;audacious2.desktop;
x-content/video-dvd=totem-xine.desktop;vlc.desktop;
x-content/audio-player=vlc.desktop;
x-content/image-dcf=shotwell.desktop;
x-scheme-handler/mailto=userapp-Evolution-S779UV.desktop;
application/x-shellscript=gedit.desktop;

---

### Post by ubunlilluz on 2011-05-16
> **mc4man said:**
> Try opening home folder (view > show hidden files) > .local/share/applications and deleting mimeapps.list
(you'll lose any file associations previously set, no big deal, they'll be reset upon use and a new mimeapps.list created

Or open it up and at the very top, _if not there,_ create a new section and add a line - 
```
[Default Applications]
inode/directory=nautilus-folder-handler.desktop

```

I'd just delete it and let a new one be created - natty uses a slightly different format where there is a [Default Applications] section and an [Added Associations] section

Ex. on a fairly new install this is the current one here

thank you mc4man, i've just deleted it and it works !

---

