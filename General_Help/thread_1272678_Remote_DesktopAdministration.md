---
title: "Remote Desktop/Administration?"
date: 2009-09-22
forum: General Help
---

### Post by ChildOfMana on 2009-09-22
Hi all,

Here's my fix; I recently re-conditioned a laptop for my cousin which she uses for work. I installed Ubuntu 9.04 on it for her and set it all up so that it would 'just work' for everything she needs it for. For the most part I succeeded. However, it has since come to light that I failed to sort a few things out and she's having a few problems doing everything she needs to do. She lives quite far away from me though and I can't get to her for a while.

I could talk her through things on the phone but it would be much, *much* easier if I could just remotely connect to her machine - with full sudo rights if possible - and make all the tweaks that way.

Is there an easy way to do this (that doesn't require much configuration on her side)?

What I need, preferably and if possible, is a way to get a graphical representation of her desktop on my screen so I can pull up a terminal (and browser if needed - for possible router configuration) and do whatever needs doing.

I realise this may not be easy (or even possible) but any help/advice will be greatly appreciated.

I've looked into VNC but to be honest I find it all very confusing.

I'm running Hardy and she's running Intrepid.

Thanks.

---

### Post by XCan on 2009-09-22
I think that you indeed can go for VNC. Either she can set it up or you can set it up for her if you have SSH (X forwarding) access. Regardless, either one of you can type ```
 vino-preferences 
``` and enable the VNC. After that you should be able to connect to her machine using a vncviewer like the one built into Ubuntu. 

Don't forget to secure it if you plan to keep it on!

---

### Post by ChildOfMana on 2009-09-23
Thank you XCan, I'll look into it.

Security isn't much of a problem as won't take me long to fix things up and shouldn't reqiure access again after that (hopefully, anyway).

I take it I'll need her IP address though? That shouldn't be a problem.

---

### Post by ChildOfMana on 2009-09-23
Okay, I can get her to allow access... but how do I connect after that? What do I use from my end to gain access?

_Edit:_ Think I've figured it out now.

Thanks

---

