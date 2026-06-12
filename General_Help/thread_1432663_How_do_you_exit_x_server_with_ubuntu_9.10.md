---
title: "How do you exit x server with ubuntu 9.10?"
date: 2010-03-18
forum: General Help
---

### Post by kind_bud on 2010-03-18
I was wondering how you exited x server in ubuntu. I relatively new to linux. I wanted to install the newest nvidia driver, and they said you needed to exit x server when running the driver installer. Someone already told me to try ctrl-alt- F6, which didn't work. That just put me in a virtual terminal that still had x-server running. So if anyone knows how to exit x-server, I would really like to know.

---

### Post by wjm on 2010-03-18
The hardware driver tool available in Ubuntu (located in System -> Administration -> Hardware Drivers) negates the necessity to do this and it also ensures you get a fresh set of drivers which are approved/tested for Ubuntu and it's X server.

If you're hard set on going this path though execute:

sudo init 1

and that should thrash the X server.  To get back in, pass along init 2 instead of 1 and you'll be back in X.

---

