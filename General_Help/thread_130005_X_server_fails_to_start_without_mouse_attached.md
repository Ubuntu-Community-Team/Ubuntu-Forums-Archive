---
title: "X server fails to start without mouse attached"
date: 2006-02-15
forum: General Help
---

### Post by DexterBelgium on 2006-02-15
Hey guys,

I'm running a Breezy box, headless. Up until a few days ago, my box would start, no problem, without a mouse attached, and just happily sit at the Gnome welcome screen. It even had a kind of keyboard-mouse, using Numpad. 

I don't know what changed (had been messing about with a few programs that went wrong), but suddenly it wouldn't start the x-server anymore, stating that there was no corepointer device. I finally got around this by adding "AllowMouseOpenFail" as an option to the Serverflags section of my xorg config file. 

However.. I lost the keyboard-mouse thingy.

I suspect that somehow, a PS/2 mouse was installed in the XORG config, and that precludes the standard mouse that is loaded. Could anyone show me their standard xorg config file (with no mouse attached), so that I can see in what it differs from mine?

BTW: I usually admin my box through xdmcp. This is not a good thing to do at a Lan Party, I know. Two questions that are kind of off my own topic:
1. what do i change to my startup to make it NOT load x-server by default, but keep xdmcp
2. what is the better way of remote graphical management-logging in-etc. FreeNX? XDMCP over SSH? ...?

Thanks for ur time reading this...

---

