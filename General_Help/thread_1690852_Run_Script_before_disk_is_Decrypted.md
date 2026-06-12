---
title: "Run Script before disk is Decrypted"
date: 2011-02-19
forum: General Help
---

### Post by brigzzy on 2011-02-19
Hey all!

I have a question that I can't find an answer to on google, so hopefully someone here will have an idea.  Here's my situation:

I have a netbook with full disk encryption (It's not really true full disk encryption, because my /boot partition is unencrypted, I'm just pretty sure that's what it's called.), that asks for a pass phrase on boot.  What I would like to do is have it run a simple bash script that echos my contact information, so that if I misplace my netbook, it can be returned to me.  Does anyone know how I would accomplish this?  I added the script to the init.d folder but since it's encrypted, it won't run before the disk is decrypted.  Is there a way I can put the script on my boot partition and have it run at boot time?

Thanks folks :D

Brigzzy

---

