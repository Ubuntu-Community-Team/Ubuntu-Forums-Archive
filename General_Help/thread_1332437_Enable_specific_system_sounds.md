---
title: "Enable specific system sounds"
date: 2009-11-20
forum: General Help
---

### Post by Xavier Oddmon on 2009-11-20
Hello! I am using Karmic Koala, and have installed the freedesktop sounds theme. In /usr/share/sounds/freedesktop/sounds, there are a number of sounds that do not play. Specifically, 
```
complete-media-burn.ogg, desktop-logout.ogg, message-new-email.ogg, trash-empty.ogg, window-move-start.ogg, window-move-stop.ogg, window-slide.ogg
```

However, I can't find a gui to enable or disable certain sounds. The sounds theme manager only allows you to enable the theme as a whole, and while that box is checked, these sounds still don't play when the various corresponding actions occur. I also could not find a key in gconf-editor, nor a dot-directory or settings file anywhere (although i could be missing it.) Is there some way to enable these? Specifically, i want to enable the window move sounds, the burn sound, and the trash sound. I have a feeling that the logout sound isn't related to this, as I haven't heard it since feisty fawn.

Also, issuing the command canberra-gtk-play --id="$SOUND" plays the corresponding sound, so it's not that the sounds are broken.

---

### Post by Giblet5 on 2009-11-20
9.10 is not an LTS release. It gets features out the door so that people like you and me can add these things in time for LTS (April).

There isn't a tool to do this yet (for Gnome - KDE, yes).

I'd step up to the plate on this one, but I really don't care about system sounds, so it would turn into a chore for me.

YOU, however.... ;)

---

