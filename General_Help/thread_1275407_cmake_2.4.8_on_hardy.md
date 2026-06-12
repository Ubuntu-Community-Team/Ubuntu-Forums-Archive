---
title: "cmake 2.4.8 on hardy?"
date: 2009-09-25
forum: General Help
---

### Post by amyhughes on 2009-09-25
I have an install script for a package that apparently requires cmake 2.4.8, and on hardy the latest available is apparently 2.4.7.

Can I install cmake 2.4.8 on hardy?
Should I install cmake 2.4.8 on hardy? :-)
How do I install cmake 2.4.8 on hardy?

I've downloaded it and the install script (the .sh version) wants to place it in a new location (a subdirectory of where I am when I install), and I don't want another copy, so if I am able to install it, and I should install it, I'm wondering how I can get it to install replacing the older version.

Or is there is an easier way to do this...

Thanks,
Amy

---

### Post by mc4man on 2009-09-25
Why don't you first see if the updated cmake in hardy-backports will suffice 
2.6.2-1ubuntu1~hardy1

( many times a requirement is an equals or greater

---

### Post by amyhughes on 2009-09-25
Is that a package name I should apt-get? If it is, do I need to add something to /etc/apt/sources.list?

sudo apt-get install 2.6.2-1ubuntu1~hardy1
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package 2.6.2-1ubuntu1~hardy1

Thanks,
Amy

---

### Post by mc4man on 2009-09-25
Sustem -> Administration -> Software Sources -> Updates

Enable ...backports, click close and reload

then ck. in synaptic or update manager

(you probably should go back to ....Software sources and disable backports after updating cmake if you tend to do 'blanket' updates thru the update manager without checking thru first

---

### Post by amyhughes on 2009-09-25
Thanks, mc4man, I now have 2.6 installed. I'll see if that works.

THanks!
Amy

---

