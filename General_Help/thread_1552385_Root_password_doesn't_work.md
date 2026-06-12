---
title: "Root password doesn't work"
date: 2010-08-13
forum: General Help
---

### Post by spoovy on 2010-08-13
I know this sounds unlikely but the root password no longer works.  I must've typed it in about a million times, I'm definately getting it right, it just no longer works.

All I did was install Slackware 13.1 onto a different partition.  This didn't touch my Ubuntu partition at all so I really don't get this at all. 

I have rebooted a couple of times but the problem remains.  What on earth is going on here and does anyone have any idea what I can do about it?

Thanks in advance

Spoov

---

### Post by lisati on 2010-08-13
The root password is disabled by default in Ubuntu. Have a look here: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by philinux on 2010-08-13
> **spoovy said:**
> I know this sounds unlikely but the root password no longer works.  I must've typed it in about a million times, I'm definately getting it right, it just no longer works.

All I did was install Slackware 13.1 onto a different partition.  This didn't touch my Ubuntu partition at all so I really don't get this at all. 

I have rebooted a couple of times but the problem remains.  What on earth is going on here and does anyone have any idea what I can do about it?

Thanks in advance

Spoov

[http://www.psychocats.net/ubuntu/fixsudo](http://www.psychocats.net/ubuntu/fixsudo)

---

### Post by spoovy on 2010-08-13
Thanks lisati, I had no idea.  I only installed ubuntu last week, and I used the graphical tools for initial admin and config to test them out.

I have been very happy with ubuntu in general so far, so it stayed on my hdd.  It never registered that I hadn't entered a root password at installation though, so it was baffling me that I couldnt become su.

Seems weird preventing root shells, but I spose ubuntu isn't aimed at superusers so I can see the reasoning.

Thanks again.

---

