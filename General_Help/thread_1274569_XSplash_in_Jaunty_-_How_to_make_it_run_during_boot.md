---
title: "XSplash in Jaunty - How to make it run during boot?"
date: 2009-09-24
forum: General Help
---

### Post by coldReactive on 2009-09-24
I installed xsplash in jaunty, but it won't run during boot.

PPA: [https://launchpad.net/~gastly/+archive/gastly-main](https://launchpad.net/~gastly/+archive/gastly-main)

How do I configure boot to have it run in jaunty? I purged usplash from my system, so its configurations are gone.

---

### Post by coldReactive on 2009-09-24
bump

---

### Post by coldReactive on 2009-09-25
bump again

---

### Post by coldReactive on 2009-09-25
another bump

---

### Post by coldReactive on 2009-09-26
Yet another bump

---

### Post by coldReactive on 2009-09-26
bump

---

### Post by coldReactive on 2009-09-26
bump

---

### Post by coldReactive on 2009-09-27
bump

---

### Post by philinux on 2009-09-27
I think it will only run in Karmic. I'm running alpha6 and it's pretty stable. It's running on my number 2 internal HD. I always have a development release on there.

---

### Post by coldReactive on 2009-09-27
> **philinux said:**
> I think it will only run in Karmic. I'm running alpha6 and it's pretty stable. It's running on my number 2 internal HD. I always have a development release on there.

But you'd think that Jaunty could be configured to boot with xsplash, since Ubuntu is "so" customizable ;) Not trying to troll or anything, but if someone offers a ppa of something that shouldn't be, they should give instructions on how to configure and use it.

---

### Post by coldReactive on 2009-09-27
bump

---

### Post by coldReactive on 2009-09-28
bump

---

### Post by CRAY-4 on 2009-09-28
there is no way, but you could install bootup manager(sudo apt-get install bum) and replace the usplash script w/ xpslash, but it shouldnt work since 9.10 has a diffrent x server and boot config

---

### Post by coldReactive on 2009-09-28
> **CRAY-4 said:**
> there is no way, but you could install bootup manager(sudo apt-get install bum) and replace the usplash script w/ xpslash, but it shouldnt work since 9.10 has a diffrent x server and boot config

But since I purged usplash, the script in bum for usplash no longer exists. How do I add a new entry in bum?

---

### Post by coldReactive on 2009-09-28
bump

---

### Post by coldReactive on 2009-09-30
Abandoning thread, I guess. *sigh* What a waste.

---

### Post by CRAY-4 on 2009-10-26
there is no way but upgrading to ubuntu 9.10:D:D:D

```
update-manager -d
``` if upgrading before oct 29

```
update-manager --dist-upgrade
``` if after oct 29

---

### Post by twright on 2009-10-26
You would have to talk to the developers as there are a lot of low level changes behind xsplash...

On the other hand, can't you just wait 2 days or grab the RC

---

### Post by coldReactive on 2009-10-26
You guys need to read when my last post was, 3 weeks ago? I abandoned the thread.

---

### Post by twright on 2009-10-26
oops, good luck anyway> **coldReactive said:**
> You guys need to read when my last post was, 3 weeks ago? I abandoned the thread.

---

