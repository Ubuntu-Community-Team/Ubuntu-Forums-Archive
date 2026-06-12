---
title: "Chrome segmentation fault on start"
date: 2012-05-20
forum: General Help
---

### Post by hotbelgo on 2012-05-20
I'm on 12.04 and for about a week Chrome will not start.
When I try it from terminal I get a simple 'segmentation fault' message, and this is what I found in syslog.

May 19 16:25:26 ------ kernel: [  213.208277] chrome[2890]: segfault at 0 ip b2a95a3e sp bfd6f250 error 4 in libc-2.15.so[b2a28000+19f000]

Help!!

---

### Post by sikander3786 on 2012-05-20
Did you try removing and re-installing Chrome? From Terminal:

```
sudo apt-get purge google-chrome-stable
sudo apt-get install google-chrome-stable
```

Or install it using the downloaded .deb package after removing it.

---

### Post by hotbelgo on 2012-05-20
Yes, and I've tried beta and unstable too. I found some complicated stuff about nscd [here]("https://bbs.archlinux.org/viewtopic.php?id=133021") but it didn't immediately help either

---

### Post by sikander3786 on 2012-05-20
Hmmmm. Sounds like a bug but it is working fine for me.

I don't have many suggestions other than trying 'chromium-browser' instead.

---

### Post by hotbelgo on 2012-05-26
A week of Ubuntu updates and still Chrome just segfaults immediately, without anything even appearing on the screen

> **hotbelgo said:**
> I'm on 12.04 and for about a week Chrome will not start.
When I try it from terminal I get a simple 'segmentation fault' message, and this is what I found in syslog.

May 19 16:25:26 ------ kernel: [  213.208277] chrome[2890]: segfault at 0 ip b2a95a3e sp bfd6f250 error 4 in libc-2.15.so[b2a28000+19f000]

Help!!

---

### Post by vasa1 on 2012-05-26
> **hotbelgo said:**
> I'm on 12.04 and **for about a week** Chrome will not start...
Was it working previously on 12.04 and then the problem suddenly started?

Have you tried renaming ~/.config/google-chrome/Default to something else just in case it is a problem with your profile?

```
sudo apt-get purge google-chrome-stable
``` won't remove your profile and so if something is corrupted in there, it will affect a new installation.

BTW, I'm using Chrome 19 on 12.04 without any problem.

---

### Post by hotbelgo on 2012-05-27
Nope - didn't help.
I tried to install nscd as i'd read about it a few times but no success. Interestingly Chromium does work.

---

### Post by hotbelgo on 2012-09-01
> **vasa1 said:**
> Was it working previously on 12.04 and then the problem suddenly started?
Yes, but now so long ago I can't recall what I might have done just before the problem started

---

