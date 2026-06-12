---
title: "Xgl and Xorg multiple instances."
date: 2006-06-11
forum: General Help
---

### Post by nanenj on 2006-06-11
I'm trying to get two X-Servers running at the same time.  Originally, when I installed, I figured out that I could have it boot only one XServer, and then get another with gdmflexiserver.   This is exactly the behavior I want.  But, ideally.  I'd love to be able to choose at bootup whether I enter an Xgl Server or normal X server, and also be able to pick from the gdmflexiserver popup what type of server.

My current setup boots me into an Xgl Server, and I can pop up a normal X server via gdmflexiserver, but, when I pick the configuration for an XGL server, it fails with a maybe the server is not configured properly, or it does seemingly nothing at all that I can tell.

Ultimately, I'd like a way to choose which X server I'm being tossed into as the initial one (I do like that only one starts at boot-up) and then also be able to pick one from gdmflexiserver.  If this can't be done, I'm just fine with booting into one, and then being able to choose what I want from gdmflexiserver.

If it helps, my current launcher for gdmflexiserver is: gdmflexiserver -l -s
When I double click that it presents me with a list of the [server-] options I have configured in gdm.conf and gdm.conf-custom.

Thanks much in advance for any help :)

---

