---
title: "FireFox and speed"
date: 2009-11-13
forum: General Help
---

### Post by Himself2007 on 2009-11-13
Hello

I have Ubuntu 9.10 and use FireFox 3.5.4.
Like its Windows counterpart, Firefox 3.5.5, all extensions are the same and all settings are quite similar.
But Ubuntu'S Firefox is quite slow compared to Windows's and especially during startups.
Any way I can accelerate all processes?
Thanks

Luc

---

### Post by winotree on 2009-11-13
**lovinglinux** has put a lot of work into this.  [http://ubuntuforums.org/showthread.php?t=1193567](http://ubuntuforums.org/showthread.php?t=1193567)   Have you seen it?

And without knowing anything else about your problem I'd bet the answer is ipv6.  :-k  ;)

---

### Post by QIII on 2009-11-13
lovinglinux has a great tutorial on FF optimization here...

[http://ubuntuforums.org/showthread.php?t=1193567](http://ubuntuforums.org/showthread.php?t=1193567)

---

### Post by lovinglinux on 2009-11-13
> **winotree said:**
> **lovinglinux** has put a lot of work into this.  [http://ubuntuforums.org/showthread.php?t=1193567](http://ubuntuforums.org/showthread.php?t=1193567)   Have you seen it?

And without knowing anything else about your problem I'd bet the answer is ipv6.  :-k  ;)

> **QIII said:**
> lovinglinux has a great tutorial on FF optimization here...

[http://ubuntuforums.org/showthread.php?t=1193567](http://ubuntuforums.org/showthread.php?t=1193567)

Thanks for pointing to my tutorial.

In regard to startup speed you should see the Database Optimization section.

Firefox startup speed is usually compromised by extensions, because Firefox needs to load all extensions pages at startup, even if they are not displayed in the browser. Sometimes extensions perform automatic functions on startup or shutdown, like reading or writing to databases. If this is the case and your database is not optimized, it takes a lot of extra time to start or shutdown.

Also make sure your sidebar is not opened during start. Depending on which sidebar is opened, it will also perform additional database reading/writing.

---

### Post by winotree on 2009-11-13
> Also make sure your sidebar is not opened during start. Depending on which sidebar is opened, it will also perform additional database reading/writing.                                                                 I didn't know that.  That's nice to know.
> Thanks for pointing to my tutorial.It easier to point to a polished piece of work than to try stumbling through a fresh attempt to explain something you only recently learned.  ;)

---

### Post by lovinglinux on 2009-11-13
> **winotree said:**
> I didn't know that.  That's nice to know.

That's something you usually realizes when you are developing extensions, specially when your own sidebar extension makes Firefox startup slower :)

> **winotree said:**
> I didn't know that.  That's nice to know.
It easier to point to a polished piece of work than to try stumbling through a fresh attempt to explain something you only recently learned.  ;)

Thanks.

---

### Post by wilee-nilee on 2009-11-13
> **QIII said:**
> lovinglinux has a great tutorial on FF optimization here...

[http://ubuntuforums.org/showthread.php?t=1193567](http://ubuntuforums.org/showthread.php?t=1193567)

The Ubuntu Geek link in the thread is what I use but generally I just load fasterfox from addons it does basically the same thing.

---

### Post by Himself2007 on 2009-11-13
Wow! Good reading!
Excellent document.
Thanks to all and especially lovinglinux!

Luc

---

### Post by lovinglinux on 2009-11-13
> **Himself2007 said:**
> Wow! Good reading!
Excellent document.
Thanks to all and especially lovinglinux!

Luc

You are welcome.

---

### Post by wilee-nilee on 2009-11-14
I used to have a bookmark on how to run firefox in ram, it might even be in your thread lovinglinux it actually made it run really fast.

---

### Post by lovinglinux on 2009-11-14
> **wilee-nilee said:**
> I used to have a bookmark on how to run firefox in ram, it might even be in your thread lovinglinux it actually made it run really fast.

Yes, it is. I use a different method, but the original thread is also linked in my tutorial.

---

