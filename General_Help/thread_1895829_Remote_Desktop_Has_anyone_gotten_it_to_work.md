---
title: "Remote Desktop: Has anyone gotten it to work?"
date: 2011-12-15
forum: General Help
---

### Post by malibu on 2011-12-15
I have not been able to get tightvnc server to work on my ubuntu 11.10 server at all.  I've tried changing my xstartup file to all kinds of things according to things I have found in Google but all I can get is a Gnome desktop with no icons, no taskbar, and no menu items.  Has anyone gotten tightvnc server to work on Ubuntu 11.10?  I don't need Unity but I would like Gnome.  On previous Ubuntus I have used two instances of tightvncserver and gotten two desktops with no issues.

At least I would like to be able to have the native remote desktop work without having to sign in on the console first.  But preferable would be to get tightvncserver to work.

If anyone can help me with either of these things please reply, thanks.

---

### Post by dan3501 on 2011-12-30
I echo malibu's sentiment.  I've been exploring 11.10, and it is appears great.  But my server is down in the basement out of the way, and it is a hassle to access the desktop directly.  I need to do this on occasion, and TightVNC does not work with this version, same issue with the menus not appearing, etc.  I'm holding out hope that there is a solution, but its looking like a downgrade to 11.04 is in the works.  

I too would be interested to know if ANYONE has got this to work in 11.10.

Dan

---

### Post by BHEJU on 2011-12-30
Try this:
When you log into server (not remotely) but physically... switch to Unity 2D (or gnome) instead of 3D from the log-in screen. and run vnc. It should work.

Cheers,

---

### Post by dan3501 on 2011-12-30
I did switch it to Gnome-classic.  Still did not work.  I will try Unity-2D and see if I get better results.

When you say that "it should work", does that mean that you got it to work on your machine?

---

### Post by malibu on 2011-12-30
My server is on ESX but I should be able to do this on the console.  Will this solution be preserved across reboots?  Part of the convienence of ESX is not really ever having to touch the console.. I usually just start multiple instances of vncserver that I want under different users with /etc/rc.local

---

### Post by BHEJU on 2012-01-04
Yes. I use Unity 2D on server. and I access it using VNC by terminal client. never have any issues.

Cheers,

---

### Post by denzelchurchill on 2012-04-01
I'm having the same issue as OP.

Fresh install of 11.10 server, installed tightvncserver, and installed gnome-core, but can't seem to get it to work at all (Chicken of the VNC on Mac OS X Lion).

Aside from installing these packages, are there any other steps we're missing? I too have tried dozens of xstartup configurations...never any luck. (Although I may be in a worse predicament...I only see black screen...no desktop whatsoever.)

Any help from people on 11.10 with VNC would be most appreciated!

---

### Post by HiImTye on 2012-04-02
occasionally I use VNC to help a friend with her laptop, hers is 11.04 and mine is 11.10. I had to make sure the correct ports were open on her router. you can always do a reverse connection too if you are unsure about the router settings

---

