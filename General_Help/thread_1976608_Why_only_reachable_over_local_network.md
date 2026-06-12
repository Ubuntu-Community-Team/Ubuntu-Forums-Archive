---
title: "Why only reachable over local network?"
date: 2012-05-09
forum: General Help
---

### Post by Scooter_X on 2012-05-09
We've probably all seen this:

> Your desktop is only reachable over the local network. Others can access your computer using the address localhost.

What's the deal with that? I know I don't have a static IP on my router but I would think that I should at least be able to use the dynamic IP (whatever it may be at the time) to connect... I would guess it's more than just whether it's dynamic or static, but what might that 'more' be?

---

### Post by 2F4U on 2012-05-09
It is a bit difficult to say anything about the problem without any context. It may be the router that is blocking access from the outside.

---

### Post by Scooter_X on 2012-05-09
Well, you actually wound up helping me a bunch. I don't know why, but I never even thought of finding out what ports would be necessary to use that, and it seems that 5900 is the one. SO, I opened it up and whamo. Now I'm good. Sortof. I do have multiple systems I'd like to remotely connect to while I'm out and about, but my particular belkin router doesn't seem to want me to open the same port for more than 1 particular IP address... Is that standard, do you know? How would a guy connect to different machines without being able to open one port for multiple IPs?

---

