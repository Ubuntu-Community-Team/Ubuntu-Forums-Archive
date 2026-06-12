---
title: "window manager sometimes won't load"
date: 2010-09-01
forum: General Help
---

### Post by watgrad on 2010-09-01
Sometimes (one boot in five?) the Window Manager fails to load at startup.  I can force it to load with Compiz Fusion menu, but would really like ubuntu to load it properly at startup.
I've attached the xsession-errors file - hoping that someone more knowledgeable than I can help me sort this out...

Lucid 64bit
Intel Quad core 2, 3 gig ram, NVidia 8400GS graphics, fresh install if 10.04

---

### Post by watgrad on 2010-09-01
bump

---

### Post by watgrad on 2010-09-11
Does anyone else experience this.  I have two computers with Ubuntu, a macbook and a desktop.  Both with fresh installs of Ubuntu 10.04.  Both experience this problem intermittently. 

Is there a way to force ubuntu to check for a running wm and then start it if it is not running after startup?

---

### Post by wojox on 2010-09-11
Are you always using Compiz? Have you installed other Window Managers?

How about going into System > Preferences > Startup Applications and adding 

```
compiz --replace
```

---

### Post by watgrad on 2010-09-11
Metacity and Compiz are the two wm installed.  Compiz is set as the default.

The code you listed, does the '--replace' argument tell the system to 'replace' the current wm with compiz?  Just so I know what is happening...

Thanks for your help!

---

### Post by wojox on 2010-09-12
> **watgrad said:**
> Metacity and Compiz are the two wm installed.  Compiz is set as the default.

The code you listed, does the '--replace' argument tell the system to 'replace' the current wm with compiz?  Just so I know what is happening...

Thanks for your help!

Yes Metacity is Gnome's window manager and --replace will 'replace' the current wm with compiz. See for yourself

```
man compiz
```

It may work it may not.

---

### Post by watgrad on 2010-09-19
Problem persists, not sure why this happens, sporadically wm doesn't start on login.

I can manually start it, but this 'bug' really bugs me - there shouldn't be such an essential component failing to start...any ideas from the experts?

---

### Post by DaveRaj on 2010-10-08
Hi, just letting you know (for the sake of solidarity :)) that I have the same problem. Since upgrading to 10.4, compiz intermittently fails to start. Admittedly so far it hasn't annoyed me enough to try to understand what's going wrong.

---

### Post by watgrad on 2010-10-08
I wonder if it is issues like this that prevent Ubuntu from going more main-stream.  Ubunutu works so well MOST of the time.  But for a non-tech oriented person to adopt it, the basic graphical user interface should always start properly.

---

### Post by DaveRaj on 2010-10-10
> **watgrad said:**
> I wonder if it is issues like this that prevent Ubuntu from going more main-stream.  Ubunutu works so well MOST of the time.  But for a non-tech oriented person to adopt it, the basic graphical user interface should always start properly.

It certainly doesn't help :(. But to be fair, these sort of bug issues are pretty rare, so I don't think they would have any real impact on uptake statistics (note: I have no evidence to back this up). Mind you, I do share your frustration that its a pretty fundamental problem that you expect to just work in a mature system.

But at the end of the day while ubuntu has commercial backing it still relies on the volunteers who are generously donating their time and expertise.

---

### Post by Lylex11 on 2010-11-18
I have the same behaviour on 10.04 x64. I can't remember if it was the same on 9.10, but I think it might have been. At first I thought it was compiz or emerald as I'd switched to emerald for a while. But changing back to compiz hasn't solved the problem at all. Does anyone know of a fix?

---

