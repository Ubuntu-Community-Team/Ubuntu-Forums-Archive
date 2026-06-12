---
title: "RAM usage?"
date: 2012-02-01
forum: General Help
---

### Post by koszta on 2012-02-01
Hi folks, 

I know that it might be normal but I am still kinda wodering if it is ok that my server has only 440 MB free RAM? Is ubuntu using it so that it doesnt have to swap ? Is it ok on a server machine?

---

### Post by Lars Noodén on 2012-02-01
It depends on what services you have running.  What do you have on your server?  The minimum system requirements for Ubuntu Server are [128 MB](https://help.ubuntu.com/community/Installation/SystemRequirements#Ubuntu_Server_.28CLI.29_Installation) of RAM.  But depending on what you are doing, you may need more.  

You can check your RAM usage with [top](http://manpages.ubuntu.com/manpages/oneiric/en/man1/top.1.html)

---

### Post by Slim Odds on 2012-02-01
This is a very commonly asked question.... [http://www.linuxatemyram.com/](http://www.linuxatemyram.com/)

The bottom line is that "free" RAM is wasted RAM.

File caching takes advantage of memory not needed for programs. If programs need it, the file cache immediately gives it up.

P.S. Windows does exactly the same thing.

---

### Post by rg4w on 2012-02-01
FWIW, I've found Ubuntu to be very efficient with making use of RAM, caching as much as is it can but releasing it as needed.  Depending on how you're viewing "available RAM", part of what you're seeing may be the cache, which likely isn't a problem.

---

### Post by koszta on 2012-02-01
thank you all very much... I thought so but wasnt sure

---

### Post by mörgæs on 2012-02-01
If this answers your question, please mark the thread 'solved'.

---

