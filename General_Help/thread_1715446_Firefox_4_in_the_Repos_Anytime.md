---
title: "Firefox 4 in the Repos Anytime?"
date: 2011-03-26
forum: General Help
---

### Post by gerowen on 2011-03-26
So when will Firefox 4 hit the repos?  I like its interface and how speedy it is, but I'm running Ubuntu 64bit with 64 bit Java/Flash, and the downloadable version of Firefox 4 (stable) is only 32bit.  When will Firefox 4 make it into the Ubuntu repos so I can just apt-get upgrade myself into faster web browsing instead of having to hassle with manually downloading 32bit Flash and Java libraries and then keeping them up to date manually, etc.?

---

### Post by Dark_Stang on 2011-03-27
[http://askubuntu.com/questions/6339/how-do-i-install-firefox-4/6348#6348](http://askubuntu.com/questions/6339/how-do-i-install-firefox-4/6348#6348)

---

### Post by gerowen on 2011-03-27
> **Dark_Stang said:**
> [http://askubuntu.com/questions/6339/how-do-i-install-firefox-4/6348#6348](http://askubuntu.com/questions/6339/how-do-i-install-firefox-4/6348#6348)

Giving this a shot now, I added this PPA a while back and it wasn't working.

This one is actually hitting the servers instead of timing out, maybe I was looking at an old one or something.  Thanks!

---

### Post by gerowen on 2011-03-27
Marking as SOLVED because it works just fine.

---

### Post by RedRat on 2011-03-27
> **Dark_Stang said:**
> [http://askubuntu.com/questions/6339/how-do-i-install-firefox-4/6348#6348](http://askubuntu.com/questions/6339/how-do-i-install-firefox-4/6348#6348)
I guess I am extraordinarily dense and it is late at night, but this did not really explicitly answer the question of which version will be installed, 32 bit or 64bit. Does Ubuntu using apt-get and update and repos "know" that you are looking for the 64 bit version. I run 10.04 LTS 64bit, and want to know if I add that repo and update it, will it install the 64bit version?

---

### Post by Vaphell on 2011-03-27
yes. i run 10.04 64bit too, updated to ff4.0 and **file firefox-bin** says
```
firefox-bin: ELF 64-bit LSB shared object, x86-64, version 1 (SYSV),
dynamically linked (uses shared libs), for GNU/Linux 2.6.15, stripped
```

---

### Post by RedRat on 2011-03-27
> **Vaphell said:**
> yes. i run 10.04 64bit too, updated to ff4.0 and **file firefox-bin** says
```
firefox-bin: ELF 64-bit LSB shared object, x86-64, version 1 (SYSV),
dynamically linked (uses shared libs), for GNU/Linux 2.6.15, stripped
```
Hey thanks! I guess I was being a bit too dense and persnickety about the reply. The way that web page answered it, it didn't really make clear what was being downloaded. I guess I should read those earlier in the day.
Thanks again.

---

