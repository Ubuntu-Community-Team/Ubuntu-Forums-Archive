---
title: "How do I get Cairo-Dock background to stay clear"
date: 2011-11-30
forum: General Help
---

### Post by TheBearNecessities on 2011-11-30
I'm running Lubuntu and have just installed Cairo-Dock.

When it first ran it had a black background so I used google and found out that i need to use gcompmgr to change my 'compositing' settings.

This works great, all i do is run gcompmgr and hit the 'compositing' button.  Bingo!  the background in Cairo-Dock is clear/transparent.

Problem is that whenever I reboot the Cairo-Dock background is black again.  This means i have to run gcompmgr and hot the 'compositing' button every time i boot into Lubuntu.

Anyone used gcompmgr before?  Anyone know how i save my gcompmgr settings so that they are permanent?

---

### Post by TheBearNecessities on 2011-11-30
I got this working by the way.

I used amethos of putting the gcompmgr into a startup file as described here: [http://ubuntuforums.org/showthread.php?t=1856701&page=2](http://ubuntuforums.org/showthread.php?t=1856701&page=2)

thanks for all your help on this thread though!  :P

---

### Post by jcoles on 2011-12-10
In the Cairo Dock configuration under System > Composition, there's an option "Emulate composition with fake transparency" which solved the problem for me. 
On my system, the black area was there even when the dock was hidden. The dock still consumes an area many times the size of the icons, but at least it fills that space with screen background now.
I didn't try installing "composition", but I'm trying to stay away from the bloat of the main Ubuntu distribution.

---

