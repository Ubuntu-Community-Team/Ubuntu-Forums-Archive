---
title: "boot console"
date: 2006-03-22
forum: General Help
---

### Post by phatbastard on 2006-03-22
Hi,

I am new to ubuntu and i wanted to give it a try since it seems it is a very popular distro right now, i have used slackware for about 3 years. My question is how in ubuntu do i change from a cool image screen when the computer boots up to a console boot. I want it to boot into console and then if i want to boot into gui i hit startx. Where is the runlevels in ubuntu?

---

### Post by trotski on 2006-03-22
You get some info in

/etc/inittab

You could probably pull kdm, etc out of one of runlevels 2-5... then set that one as default.

---

