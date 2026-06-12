---
title: "Libtag doesnt work with WMA, anyone know a workaround?"
date: 2006-04-14
forum: General Help
---

### Post by John64 on 2006-04-14
I have my entire collection of CD's in WMA lossless and it would be a pain to have to re-rip them when the only thing that doesnt work is tagging.  I belive the version of libtag1c2 1.4 is capable of it, as i read somewhere Amarok 1.4 will support it, but due to an old version of libtag, it wont work on breezy.  Can someone clarify this issue please?

EDIT:  BTW i am using Amarok in Gnome, as its the best of both worlds :P

---

### Post by Mr. Polite on 2006-04-14
libtag doesn't have the included meta data to include .wma audio in your amaroK collection. I've compiled a patched version of libtag 1.4 with .wma support, though I'm still very new and haven't quite figured out how to replace my existing libtag with my patched version.

If you do
```
sudo apt-get install amarok-xine
```
and switch amaroK to the xine engine, you will be able to play .wma, you just won't be able to add the songs to your collection until you figure out how to use the patched libtag.

I compiled a .deb for it, but I'm not at home right now to send it.

---

