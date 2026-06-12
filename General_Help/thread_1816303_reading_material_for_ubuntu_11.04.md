---
title: "reading material for ubuntu 11.04"
date: 2011-08-01
forum: General Help
---

### Post by takhar25 on 2011-08-01
hi folks,

i am brand new to ubuntu 11.04. i am required to know linux for new job mostly how to navigate the basics, i am running ubuntu 11.04 as dual boot with windows 7.

i consider my self an advanced windows user with over 10 years exp in IT field but new to linux.

i am up and running. i have two concerns.

1. what is a good book to get that not only tells u all about linux basics and command line stuff but also ubuntu.

2. i can't get onto the internet from ubuntu. i am able to connect wifi to my router and get an ip but it won't connect. i have auto matic dhcp enabled its getting an internal ip but failng to connect to any urls? i would like to have the internet working while using ubuntu so i can referne back and forth instead of using windows..

thx

---

### Post by jerrrys on 2011-08-02
here's a few links

[http://ubuntuforums.org/showthread.php?t=1756183&page=2](http://ubuntuforums.org/showthread.php?t=1756183&page=2)

[http://ubuntuforums.org/showthread.php?t=1748046](http://ubuntuforums.org/showthread.php?t=1748046)

[http://ubuntuforums.org/showthread.php?t=1756183](http://ubuntuforums.org/showthread.php?t=1756183)

[http://ubuntuguide.org/wiki/Ubuntu:Natty](http://ubuntuguide.org/wiki/Ubuntu:Natty)

---

### Post by dj722000 on 2011-08-02
When I set up my Ubuntu, I had alot of problems with getting on using my wifi. I am not saying you have the same problem as me but did you try this command in terminal: rfkill list all

0: phy0: Wireless LAN
Soft blocked: no
Hard blocked: no

Both of these should be no, otherwise it is shut off.
If anything is yes, they need to be turned to no.
I believe the command for that is:

sudo rfkill unblock all

May not fix your problem, but at least, now you know how to check it for future references.

---

