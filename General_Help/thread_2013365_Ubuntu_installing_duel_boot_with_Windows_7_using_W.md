---
title: "Ubuntu installing duel boot with Windows 7 using Wubi Help"
date: 2012-06-30
forum: General Help
---

### Post by AbhiKap on 2012-06-30
Hello,

I have Windows 7 installed on my laptop and am planning to get Ubuntu dual boot alongside Windows 7 using Wubi. I have 226 GB of free Space on my C drive. How much space should I give when it asks in the options of Wubi. I was thinking 6GB is that good enough? Also, I tried installing it on another computer which was a netbook, and I chose 5GB, it installed and but it only works when you start it the first time, after that it just gives a blank screen. 

Thanks, Help is appreciated.

---

### Post by bcbc on 2012-06-30
If you're just seeing how Ubuntu works, then 6GB is okay, but you can't do much with that. If you also want to try out a bunch of software etc. you'll need more. You can go up to 30GB.

You can (and should) keep your important data stored on the /host partition (the windows partition you installed on) or otherwise backed up regularly. 
Avoid hard shutdowns. Use [REISUB]("http://en.wikipedia.org/wiki/Magic_SysRq_key#Uses") instead.

---

