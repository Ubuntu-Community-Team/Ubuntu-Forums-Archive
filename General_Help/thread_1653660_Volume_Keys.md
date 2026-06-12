---
title: "Volume Keys"
date: 2010-12-27
forum: General Help
---

### Post by roobinatube on 2010-12-27
Im confused, please help.

Trying to get my volume up/down keys to work, when I use the lubuntu-rc file, I can make other shortcuts work, but not the volume keys. So i created ~/.Xmodmap and mapped my keys but it still didnt work.

When i type xev and press the volume buttons I get the right result, XF86AudioRaiseVolume, but the volume is not raised.

I then used xbindkeys, which worked... but for some reason when xbindkeys is running, it stops and application shortcuts, e.g. CTRL-F for find in firefox.

Anyone got any suggestions?

Thanks
Roob

---

### Post by roobinatube on 2010-12-27
Ignore this, I simply didnt notice there are default keybindings in xbindkeys using some key combinations already. Deleted these and it all works.

Still weird how xbindkeys recognises the keys but openbox doesnt... It recognises all my special keys brightness, stop, play, skip, touchpad off, etc. just not volume!

Roob

---

