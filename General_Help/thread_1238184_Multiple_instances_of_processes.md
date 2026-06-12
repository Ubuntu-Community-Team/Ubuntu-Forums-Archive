---
title: "Multiple instances of processes"
date: 2009-08-12
forum: General Help
---

### Post by fela on 2009-08-12
Often times when I check htop or the gnome system monitor, I find multiple instances of processes, varying from just a few to many (10+). They're not just daemons, it occurs on everything from ruby, python, to pidgin and firefox etc. They always have similar (but never same) PIDs, often just one number up/down. They sometimes (maybe always - haven't checked everytime) have exactly the same CPU usage, so appear to be the same thread.

PS. I have a dual core CPU, don't think it counts, but it might be a bug with SMP or something.

It's no worry as it doesn't seem to be causing any problems, I'm just wondering what's going on here. It also happens on my Ubuntu server, which has a single core (oh, that probably debunks the SMP theory huh?). Things like 7 'getty' or 'gmediaserver' or 'mysql' processes at once.

---

### Post by 3rdalbum on 2009-08-12
The "getty" ones are not out of the ordinary - they are actually the terminals you can access with Control-Alt-F1, F2 etc.

MySQL probably splits itself into separate processes for efficiency and safety, so I wouldn't read much into that. And if you have a Python program that uses multi-processing in the same way, then you'll get multiple processes of Python. Same probably with gmediaserver, to serve multiple clients at a time.

---

### Post by fela on 2009-08-12
> **3rdalbum said:**
> The "getty" ones are not out of the ordinary - they are actually the terminals you can access with Control-Alt-F1, F2 etc.

MySQL probably splits itself into separate processes for efficiency and safety, so I wouldn't read much into that. And if you have a Python program that uses multi-processing in the same way, then you'll get multiple processes of Python. Same probably with gmediaserver, to serve multiple clients at a time.

Thanks for that. Actually I am a bit skeptical about the gmediaserver thing, as I checked on a windows client (my dad's laptop) and sure enough, there were about 10 or so different gmediaservers in 'my network places'. I'm not too anxious to get it sorted though, as for one thing gmediaserver isn't even used right now. It seems to be working OK, so I'll just leave it how it is.

---

