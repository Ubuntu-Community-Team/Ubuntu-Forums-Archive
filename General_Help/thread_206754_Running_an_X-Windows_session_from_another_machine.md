---
title: "Running an X-Windows session from another machine"
date: 2006-06-30
forum: General Help
---

### Post by MoreBikesFewerCars on 2006-06-30
I have two Ubuntu machines. One (5.10) is a desktop workstation and the other (6.06) is a server. I mostly use SSH to work on the server. However, sometimes I would like to sit at the workstation and run an X-Windows/Gnome session that allows me to run software on the server. How do I set this up?

I know that VNC is available, but I want different users to be able to view their own profiles on the server. I also don't want to leave the server logged in.

Thanks.

---

### Post by invalid on 2006-06-30
[QUOTE=MoreBikesFewerCars]I have two Ubuntu machines. One (5.10) is a desktop workstation and the other (6.06) is a server. I mostly use SSH to work on the server. However, sometimes I would like to sit at the workstation and run an X-Windows/Gnome session that allows me to run software on the server. How do I set this up?

I know that VNC is available, but I want different users to be able to view their own profiles on the server. I also don't want to leave the server logged in.

Thanks.[/QUOTE]
[http://www.vanemery.com/Linux/XoverSSH/X-over-SSH2.html](http://www.vanemery.com/Linux/XoverSSH/X-over-SSH2.html)

---

### Post by MoreBikesFewerCars on 2006-06-30
Very cool. I have it working.

Any suggestions for a Windows X server? I've tried Xming, but can't get it to run Gnome. The instructions on the site are very dense|confusing|unhelpful.

---

