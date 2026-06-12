---
title: "Is remote development over VNC using local devices possible?"
date: 2011-05-12
forum: General Help
---

### Post by Lenaxia on 2011-05-12
Hey guys,

I'm looking to convert my HTPC into a remote android dev server for my girlfriend and myself, however I want to make sure that it is possible to do what I am looking to do. 

Is it possible to map local devices to the VNC server (such as an android phone) so that we can work on development over VNC with phones we have on our client computers? 

I know its a trivial matter to map local drives over VNC, but what about non-HD devices, can I still maintain full functionality as if the device itself was plugged directly into the server? 

I'll be installing ubuntu again this weekend, never got around to it after my last HD failure.

---

### Post by doas777 on 2011-05-12
no, vnc is a far simpler protocol than that, and will not abstract away the physical location of peripherals.

there is a support request to add that functionality to NX server (ubuntu can use FreeNX) but it does not appear to be complete.

---

