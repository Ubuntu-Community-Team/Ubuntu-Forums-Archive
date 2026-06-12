---
title: "speed up X forwarding over ssh?"
date: 2012-10-11
forum: General Help
---

### Post by SlugSlug on 2012-10-11
Is there any way to speed up X forwarding? I am using xming on windows and putty.

I've tried with and without compression it's really really slow & my upload is 10Mb

---

### Post by cjhabs on 2012-10-11
That is what I found when running over a WAN - I now use NXServer/NXClient - it works great over a remote connection

---

### Post by SlugSlug on 2012-10-12
Just looking for some info on this - it's not in the repos is it like VNC?

---

### Post by cjhabs on 2012-10-12
No, but there are 32 and 64 bit deb packages available - check out [www.nomachine.com](www.nomachine.com)

---

### Post by markbl on 2012-10-12
Just use VNC forwarded over ssh. Has always worked well for me for about the last 10 years. Look at x11vnc if you want to VNC your default server session. I have found the nx stuff annoying and you will notice it has never really caught on mainstream.

---

