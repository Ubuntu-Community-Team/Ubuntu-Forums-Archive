---
title: "http macros"
date: 2010-11-10
forum: General Help
---

### Post by lorderico on 2010-11-10
Hi all,

I am looking to make a macro that will log me in on a website whenever I connect to the internet.  Specifically, this macro has to input a username and password, and then press the login button.  Is there any way to do this?

Thanks,
Eric

---

### Post by Ancanus on 2010-11-10
I know that [WiCD]("http://wicd.sourceforge.net/moinmoin/Adding%20pre%20and%20post%20(dis)connection%20scripts") allows you to run scrips after it has connected to a network.

You would then write some .sh file that would probably use something like [curl]("http://curl.haxx.se/docs/httpscripting.html") to do the login.

---

