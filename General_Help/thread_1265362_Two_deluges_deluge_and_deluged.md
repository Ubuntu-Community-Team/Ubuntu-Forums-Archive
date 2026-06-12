---
title: "Two deluges: deluge and deluged?"
date: 2009-09-13
forum: General Help
---

### Post by afeasfaerw23231233 on 2009-09-13
Just wonder why there are two deluges running at the same time. 
Are they different processes?
```
25586    20   0  255m  63m 4500 S  7.0  6.4   0:50.87 deluged            
25572    20   0  390m  38m 9860 S  4.7  3.9   1:06.67 deluge  
```

---

### Post by FuturePilot on 2009-09-13
Yes, they are different processes. Deluge uses basically a thin client model. It runs as a daemon (deluged) and then you connect to the daemon from a front end (deluge). What's nice about this is that you can run the daemon on a dedicated server and connect to it though the GTK interface.

---

### Post by afeasfaerw23231233 on 2009-09-13
Thanks for explanation!

---

### Post by binbash on 2009-09-14
deluged is a daemon and deluge is its front-end.

---

### Post by nimajiman on 2009-10-19
> **binbash said:**
> deluged is a daemon and deluge is its front-end.

Can I just clarify. Does this mean I can have the daemon (**deluged**) running on my desktop computer, and then connect to it from another computer on the same LAN (i.e. my laptop) using the web ui?

If so how do I go about doing this?

---

### Post by renkinjutsu on 2009-10-19
yup! that's right..

edit: you can even connect remotely if you allow it

---

### Post by [h2o] on 2009-10-19
It doesn't even have to be the web-ui. YOu can attach the GTK UI over LAN (or WAN) as well. I do this at home and it is great!

---

### Post by NCLI on 2009-10-19
Is there a guide detailing how you'd do that?

---

### Post by nimajiman on 2009-10-19
> **NCLI said:**
> Is there a guide detailing how you'd do that?

I'll second that... A simple guide would be really handy. The official FAQ at [http://deluge-torrent.org/](http://deluge-torrent.org/) doesn't really offer much.

Running the latest version (1.2.0_RC1).

---

### Post by falconindy on 2009-10-19
The latest version appears to be buggy (at least from what I've seen). The way you would (normally) do this is, from Deluge:

Edit -> Preferences -> Interface -> uncheck 'Classic Mode'

This basically forces the gtk GUI into the thin client model. The next time you open either GUI, you'll be presented with a connection manager and a choice of server to connect to. This is where it seems to be buggy (as of the RC). You should be able to connect to the daemon and go about your business. Maybe its just me...

---

### Post by 23meg on 2009-10-19
If you follow [these steps]("http://dev.deluge-torrent.org/wiki/UserGuide/ThinClient"), it should work.

---

### Post by NCLI on 2009-10-19
I love you :D

My media server is now much moire useful, *and *I save a lot of money on power now that I only have one computer(the server) downloading torrents all the time :D

---

### Post by =NickJ= on 2009-10-20
> **falconindy said:**
> The latest version appears to be buggy (at least from what I've seen). The way you would (normally) do this is, from Deluge:

Edit -> Preferences -> Interface -> uncheck 'Classic Mode'

This basically forces the gtk GUI into the thin client model. The next time you open either GUI, you'll be presented with a connection manager and a choice of server to connect to. This is where it seems to be buggy (as of the RC). You should be able to connect to the daemon and go about your business. Maybe its just me...

I'm glad someone else is having problems, both my home server and work PC have just updated to 1.2.0 RC1 and neither of them can now connect to their daemons. I think they split deluged into a package of it's own and forgot to add the dependency or something, I'm trying to reconfigure it now from scratch.

EDIT: Holy crapola it's completely different! Just killed everything, installed individual deluged package, ran deluged then deluge --ui web and it's completely changed, about 100x better. Fantastic I love this program :D

---

### Post by falconindy on 2009-10-20
> **=NickJ= said:**
> I'm glad someone else is having problems, both my home server and work PC have just updated to 1.2.0 RC1 and neither of them can now connect to their daemons. I think they split deluged into a package of it's own and forgot to add the dependency or something, I'm trying to reconfigure it now from scratch.

EDIT: Holy crapola it's completely different! Just killed everything, installed individual deluged package, ran deluged then deluge --ui web and it's completely changed, about 100x better. Fantastic I love this program :D
Nice catch! I had attempted to install deluged after noticing that it wasn't present, and apt wanted to uninstall deluge! After that I just put it aside for the time being since Deluge itself wasn't being problematic. Removing deluge, then installing deluged and deluge individually (and in that order) fixed it!

(and yes, the new web UI is like a pritty pritty princess)

Thanks!

---

