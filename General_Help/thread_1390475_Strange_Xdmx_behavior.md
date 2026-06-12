---
title: "Strange Xdmx behavior"
date: 2010-01-25
forum: General Help
---

### Post by EdwardMorris on 2010-01-25
Hi all,

   Just another ambitious pursuit. I am trying to get dual displays working with Xdmx. I have a laptop running 9.10 and a desktop running 8.04. After hours of googling, I found out that the only stable version of xdmx that actually works is the etch5 version, so I installed it on both the machines. Also, I took care of all the usual steps like xhost +, enabling TCP port forwarding etc. etc. and managed to get a xineramic extended desktop by running

Xdmx :1 +xinerama -display :0 -display client_ip:0

Both machines have ATI cards, and this only works when I run it from 8.04 machine, but seg faults when I try it from 9.10 even with the etch5 package.

So my question is, how can I actually make it run from my laptop (9.10) and have the desktop (8.04) as a second monitor and most importantly not just a blank X screen, but an actual gnome-session???

---

### Post by tba967 on 2010-02-13
I am attempting a similar setup, however both of my machines are running 9.1.  I am also getting the segfault error.  I would be keen to know a way to do this.  I think its going to be an extremely useful setup if I can ever make it work.

---

### Post by tba967 on 2010-02-14
it turns out that there is a patch for xdmx available at [https://launchpad.net/~rdoering/+archive/xdmx-fix](https://launchpad.net/~rdoering/+archive/xdmx-fix)

the patched xdmx isn't perfect but it is usable on 2 machines running karmic.  i did find it to be very slow and choppy.  also when you leave the multihead server, keyboard function changes, hence my poor grammar in this post.

---

