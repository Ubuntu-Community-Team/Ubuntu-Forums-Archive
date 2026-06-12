---
title: "filesystem directory error"
date: 2011-01-01
forum: General Help
---

### Post by DocMindie on 2011-01-01
I've installed gtkPod for transferring music and other stuff to me iPod. Not really a surprise, eyh? I've used this software before with no problems, however this time around I've got a weird error:

the drawer /hom/<user>/.gvfs" is unwriteable. I've checked with MidnightCommander (using su access so should've be able to change waht's needed to be changed of permssions) and with just about every other tools I can think of. 

Strange thing is, the ./gvfs is not showing up in the drawer area of MC, but in with the normal files, in red. And yet, when trying to just using "return"-key, it says "cannot change drawer." even with "su chown <user> .gvfs" and trying to move it in MC results in "error 13"

Also, I'm using Midnight for this sort of work because I find it to be easier than utilizing stuff like Krusader or even the commandline tools... MC is wonderful and far morre alike my old Amiga-tools in operation than the simple text-console interface suggests :lol

This is all in all kinda frustrating as I want some music on me iPod ;)

---

### Post by calavier62 on 2011-01-01
I've had issues like that with gtkpod before; that's why I use rythymbox :D.
No, that's not a good answer. The thing is, is that .gvfs is a virtual desktop for gnome, and it allows for local HAL integration and stuff... that's not a good error to see...

I haven't seen THAT error, but the only thing that comes to my mind right now, would be to reinstall gnome (if that is possible, or maybe it's just the fact that it's 3 am) using get-apt.

good luck.

---

### Post by DocMindie on 2011-01-01
Well... as I just said, I use XUbuntu, with XFCE, not Gnome.... 

Though, mayhaps I should install the Gnome just to see if that "fixes" the problem, is that what you mean?

---

