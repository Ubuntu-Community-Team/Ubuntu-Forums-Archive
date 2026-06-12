---
title: "Problem when unmounting USB flash Stick"
date: 2006-02-07
forum: General Help
---

### Post by wilsonisme on 2006-02-07
Okay, I have a ipod shuffle (essentially a glorified usb flash drive). It mounts fine, it works with GTKpod, etc etc etc. However, when it is time to unmount it, I right click the drive's icon on my desktop, click unmount volume, the icon goes away, but I am left with an error that says "Unmount Error: Unable to eject media. Eject: unable to eject, last error: Invalid argument"

Now am I being stupid and this means it works fine, but is telling me it simply can't physically eject the USB drive? (Obviously it can't)

If this is the case, how do I prevent this annoying error from popping up every time I unmount it? Thanks!

Also one other question: Why is it I can not listen to music and play a game at the same time? I can only get one to play their sound at a time. XMMS is even more frustraiting when it comes to this, it feeds me sound errors like three times then it suddenly works. All other music players will always work, but if I have music playing then launch a game, I hear the music and not the game sound =\

---

### Post by dcstar on 2006-02-08
[QUOTE=wilsonisme]Okay, I have a ipod shuffle (essentially a glorified usb flash drive). It mounts fine, it works with GTKpod, etc etc etc. However, when it is time to unmount it, I right click the drive's icon on my desktop, click unmount volume, the icon goes away, but I am left with an error that says "Unmount Error: Unable to eject media. Eject: unable to eject, last error: Invalid argument"

Now am I being stupid and this means it works fine, but is telling me it simply can't physically eject the USB drive? (Obviously it can't)

If this is the case, how do I prevent this annoying error from popping up every time I unmount it? Thanks!
.......[/QUOTE]
What does this show:

sudo sysctl -a | fgrep eject

---

