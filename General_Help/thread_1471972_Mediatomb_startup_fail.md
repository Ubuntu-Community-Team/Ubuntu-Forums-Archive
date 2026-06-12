---
title: "Mediatomb startup fail"
date: 2010-05-04
forum: General Help
---

### Post by CODplayinFOOL on 2010-05-04
Question 1: whenever I boot the Linux machine I recently put together I see "ok" on all the startup items except Mediatomb. It always reads: "Starting upnp media server mediatomb [fail]."

So I run it myself via sudo /etc/init.d/mediatomb start
In the mediatomb default file NO_START is set to "no," hence why it tries. But why does it fail? The guide I followed to install it intended for it to run at startup, but it just fails.

Question 2: When I manually start mediatomb, and I later access it on another machine via the browser, it's all good. But on the monitor of the linux machine the command line goes bye-bye. It's just a cursor, and commands don't execute. Is there a keyboard combo like ctrl+alt+f-something that brings it back?

---

### Post by CODplayinFOOL on 2010-05-04
Per the suggestion of the Mediatomb FAQ and another thread on here I've tried:

```
sudo update-rc.d -f mediatomb remove
sudo update-rc.d mediatomb defaults 99
```

Still fails.

---

### Post by CODplayinFOOL on 2010-05-04
Well, I've been searching here and elsewhere all night to no avail. I give up on question 1. But what about question 2. When I manually start Mediatomb at the command line it never goes back after it's done. I just end up with a blinking cursor.

---

### Post by pereclies on 2010-11-11
> **CODplayinFOOL said:**
>  When I manually start Mediatomb at the command line it never goes back after it's done. I just end up with a blinking cursor.

Don't know if you're still looking for the answer to this question, but I think what you're asking is how to launch it in daemon mode.  if you launch it like
```
mediatomb -d
```
then it will show the initial startup messages and then return to the command prompt, running in the background.

---

