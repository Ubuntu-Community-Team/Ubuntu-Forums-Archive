---
title: "techniques to speed up jaunty?"
date: 2009-08-31
forum: General Help
---

### Post by uschxc on 2009-08-31
So before this version with its major boot-time decrease, I'm wondering what previous speed increase mechanisms can still be used and which are already implemented in addition to any I'm not aware of.  

I currently use preload, but am curious about prelink.  I also came across a blog entry a long time ago and supposedly allowed services to start in parallel if possible by changing switching a value in a file like rc.local or the bash.rc but I can not remember.

Since the dev team, people much smarter with linux than me, put so much time trying to make the system boot faster, is there anything an average user _should_ do to enhance performance?  I used to use noatime and norelatime to speed up hdd performance but I believe ext4 doesn't support them and is about as fast as its going to get but I would love to be proven wrong.

thoughts?

---

### Post by oldos2er on 2009-08-31
> **uschxc said:**
>   I also came across a blog entry a long time ago and supposedly allowed services to start in parallel if possible by changing switching a value in a file like rc.local or the bash.rc but I can not remember.


 You're referring to CONCURRENCY=shell, in the file /etc/init.d/rc. By default CONURRENCY is set to none, but if you have more than one processor (e.g. a Core2Duo, or greater) changing to shell will allow services to load concurrently.

 If you google "ubuntu speed up", you'll find there are many tweaks you can play with to optimize Ubuntu. Just be careful; make backup copies of any configuration files you change.

---

### Post by scouser73 on 2009-08-31
> **uschxc said:**
> So before this version with its major boot-time decrease, I'm wondering what previous speed increase mechanisms can still be used and which are already implemented in addition to any I'm not aware of.  

I currently use preload, but am curious about prelink.  I also came across a blog entry a long time ago and supposedly allowed services to start in parallel if possible by changing switching a value in a file like rc.local or the bash.rc but I can not remember.

Since the dev team, people much smarter with linux than me, put so much time trying to make the system boot faster, is there anything an average user _should_ do to enhance performance?  I used to use noatime and norelatime to speed up hdd performance but I believe ext4 doesn't support them and is about as fast as its going to get but I would love to be proven wrong.

thoughts?


You should check this port out: [[COLOR="Red"]**How To: Speed Up Ubuntu**[/COLOR]]("http://ubuntuforums.org/showthread.php?t=89491") I know it's dated November 12th, 2005 but it is relevant.

---

### Post by uschxc on 2009-08-31
i came across that post already, it led me to my initng researching.  since that post is of 05 i am curious if initng is still considered young or quasi-experimental.  it looks like its more involved than i really want... but then again so it that post involving changing system service startups.  i'll get to one or the other sooner or later i'm sure, but does anyone know where initng is maturity wise?

---

### Post by anujpathania on 2009-08-31
Also be cautious while applying tweaks, some nasty ones can cause your Linux to kaboom.

Personally I think, Ubuntu boot is fast enough for me.

---

### Post by uschxc on 2009-08-31
> **anujpathania said:**
> Also be cautious while applying tweaks, some nasty ones can cause your Linux to kaboom.

Personally I think, Ubuntu boot is fast enough for me.

thats the kind of post someone's going to come across in 10 years on an 2000 archive and laugh ;)

there's never fast enough!

---

