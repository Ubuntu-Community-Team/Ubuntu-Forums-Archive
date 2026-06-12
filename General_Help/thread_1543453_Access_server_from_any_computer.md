---
title: "Access server from any computer?"
date: 2010-08-01
forum: General Help
---

### Post by randumnumber on 2010-08-01
Hello first let me explain the situation i would like to use this in. I think this is the best way for people to understand what my end goal is.

I would like to have a server set up at home and be able to access it using a front end that i would boot from a USB drive. The reason i would do this is because at my university all of the computers are horribly slow, i have a server at home that is fast, I would sit down at one of the computers use a USB drive to boot up the computer and use it as a front end, the computer at home would be the backend. Is this doable? if so how?

---

### Post by Barrucadu on 2010-08-01
Yes; set up an SSH server daemon on your home server and connect to it remotely. You can tunnel X programs over ssh, but I imagine network lag would be more of a problem than the speed of your server for such a thing&#8230;

---

### Post by Joe of loath on 2010-08-01
You would be better off running something lightweight off the USB stick, like puppy Linux. I can't see the internet being fast enough to cope with a whole VNC session over SSH, or something similar.

Unless of course, your server is on the university internet. Last I was at a university, the internet speeds were about 30 megabits over wireless!

---

