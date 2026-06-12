---
title: "system crashing segfault error in messages"
date: 2009-10-18
forum: General Help
---

### Post by supertimmy on 2009-10-18
Hi all,

I am having some rather serious isues at the momenet with Ubuntu crashing. Applications will at random close while in use, Ubuntu will log me out or the system will freeze completely with the caps and scroll lock keys flashing.

An example of what I am seeing in the messages when it dies:

> Oct 18 17:01:12 lithium kernel: [ 5786.312017] vlc[19787]: segfault at b7f70430 ip b7f70430 sp af8fe1c4 error 4
Oct 18 17:13:23 lithium kernel: [  493.307972] compiz.real[3500]: segfault at 19e60 ip b75b6108 sp bfbec570 error 4 in libGLcore.so.180.44[b6b7c000+d1a000]
Oct 18 17:13:59 lithium kernel: [  529.037436] vlc[3674]: segfault at 243489ff ip 243489ff sp ad7ff09c error 4
Oct 18 17:42:27 lithium kernel: [ 1519.219906] gnome-panel[5032]: segfault at 0 ip b7f1643a sp bfd79aa0 error 4 in libbonobo-2.so.0.0.0[b7ef1000+52000]
Oct 18 17:42:27 lithium kernel: [ 1519.261643] trashapplet[5065]: segfault at 0 ip b7b1a43a sp bf919210 error 4 in libbonobo-2.so.0.0.0[b7af5000+52000]It sounds like a hardware problem to me but I have got a new hardrive and installed Ubuntu 9.04 with none of the updates and am having the same issues. I have tried removing one of my two DDR DIMMS and leaving the other in and I get the same issue regardless of which one I leave in.

Any help of direction would be greatly appreciated.

---

