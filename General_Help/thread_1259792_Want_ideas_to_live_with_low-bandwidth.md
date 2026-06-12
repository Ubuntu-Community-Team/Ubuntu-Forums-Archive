---
title: "Want ideas to live with low-bandwidth"
date: 2009-09-06
forum: General Help
---

### Post by MoebusNet on 2009-09-06
I typically access the internet through public wireless routers that share connections with as many as 30 wireless clients at a time. Getting a dedicated broadband connection for myself isn't really an option.

What can I do to optimise the little bandwidth I can access? I typically seem to achieve about 500-1000 kbs.

Suggestions welcomed.

---

### Post by nateperson on 2009-09-06
Depends on what you wanna do.

Installing NoScript and Adblock will help with basic surfing, but 500kbs should be good for basic surfing anyway.

---

### Post by jerrrys on 2009-09-06
don't know if will help, but...

[http://ubuntuforums.org/showthread.php?t=1193567&highlight=FOT004](http://ubuntuforums.org/showthread.php?t=1193567&highlight=FOT004)

---

### Post by ecmatter on 2009-09-06
Five-hundred kb/s is considered low bandwidth?

---

### Post by MoebusNet on 2009-09-06
I suppose you're right, if all I need to do is check my email or load a static web page. But that download speed is an average; sometimes a minute or two goes by with no data transfer at all. Makes streaming audio (Shoutcast) or video (Hulu) unbearable at times.

---

### Post by MoebusNet on 2009-09-06
> **jerrrys said:**
> don't know if will help, but...

[http://ubuntuforums.org/showthread.php?t=1193567&highlight=FOT004](http://ubuntuforums.org/showthread.php?t=1193567&highlight=FOT004)

Thanks for the link!

BTW, here is my Speedtest rating.

---

### Post by lykwydchykyn on 2009-09-06
- Install a proxy server to cache commonly used net files.  Maybe squid.
 - Install a caching DNS service to reduce DNS lookups.  Dnsmasq is a good option.
 - Setup cron-apt to fetch updates in the middle of the night, so you don't have to download them manually.

---

