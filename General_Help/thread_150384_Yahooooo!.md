---
title: "Yahooooo!"
date: 2006-03-25
forum: General Help
---

### Post by hglb on 2006-03-25
I am completly new to this linux thing. I'm trying to learn fast but I can't figure out why my ymessenger won't work. I installed it 2 days ago and it was working fine. now when i try to run it I get this:
root@Family:/# usr/bin/ymessenger
Segmentation fault

I've tried removing it and reinstalling but i get the same thing. I'm so used to point and click this OS is confusing as hell to me lol. Im running Ubuntu Breezy Badger. Any help Would be greatly appreaciated.

---

### Post by LadyDoor on 2006-03-25
I'm not expert either, but...

1) Have you tried under your regular username? Being root can be dangerous...

2) Have you tried GAIM? I don't really know about ymessenger for linux, but I *do* know for a fact that GAIM (which I think may come installed, otherwise you can get it from synaptic or by...

```
sudo apt-get install gaim
```

...) does definitely let you make and use yahoo messenger (and aim and other protocols) accounts really easily.

I hope that helps!

--Door

---

### Post by 3rdalbum on 2006-03-25
When you removed it, did you do a "Complete Removal"? That will get rid of the configuration files as well, which will often solve problems.

Unfortunately, "Segmentation Fault" can mean just about anything. Try using Gaim: It's in Applications > Internet > Gaim Instant Messenger.

---

### Post by nickj6282 on 2006-03-26
I second the GAIM suggestion. The Unix/Linux version of messenger from Yahoo is total crap. You're lucky you got it to work at all. Gaim is where it's at. I even use it on Windows now because it lets me log in to 2 yahoo, 2 MSN, an AIM, an ICQ account, and a google talk account all simultaneously.

Good luck
-Nick

Also, someone out there did make a debian package for Gyach, which is a yahoo only messenger client that works with voice, webcams, and some IMVironments. You'd have to google around for it to find it but it's out there. It's not as stable as Gaim either, but it does support a lot of things that Gaim doesn't (yet).

---

### Post by hglb on 2006-03-26
Thanks. Like I said i'm a complete newbie so I didnt know about gaim but it works great!

---

