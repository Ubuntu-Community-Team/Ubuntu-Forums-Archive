---
title: "How to setup old school vnc"
date: 2009-11-20
forum: General Help
---

### Post by r0g on 2009-11-20
Hi,

For a long time it always frustrated me that most linux VNC servers would give you your own little basic xsession when my most common use case was to want to remotely control the default desktop session.

With Ubuntu's System/Preferences/Remote Desktop it seems I got what (I thought) I wanted.

Of course now I've changed my mind!

I've acquired a VERY old mini laptop, it's an MMX233 w/ 128Mb of RAM (sadly soldered to the motherboard w/ no upgrade slot!). There's no way it'll run Ubuntu but it seem relatively happy with DSL4.x (Damn samll linux) so I figured I could use it to control a media player on my main machine giving me the ability to start and stop my podcasts without having to KVM back to said machine (I have a trusty but SLOW KVM switch too!).

Now I don't want to remotely control my high rez, compiz enabled 3d accelerated desktop via a slow old laptop with a dingy little screen. Out of curiosity I tried it anyway and it doesn't really work (probably compiz I guess) so it's irrelevant...

I'd like Ubuntu to offer VNC it's own very basic X session like you used to get in the good old days (grey background, one x-term) but I don't see anywhere I can tell it to do that :(

Can I get the Ubuntu default VNC server to offer this kind of session by editing some config files? or might I need to install a different VNC server?

Thanks for any suggestions :)

Roger.

---

### Post by bodhi.zazen on 2009-11-20
Install a different VNC server, such as vncserver

Or better , learn to use ssh -X

---

### Post by stonebit on 2009-11-20
I use SSH to connect, then forward the x session to the client with vnc. Install SSH and vncserver on the server side and vncviewer on the other side.

---

