---
title: "installing xorg from 8.04 on version 9.10"
date: 2009-11-04
forum: General Help
---

### Post by lunaparadox on 2009-11-04
I need to downgrade xorg so I can get xinerama working with 2 graphics cards. thanks.

---

### Post by Giblet5 on 2009-11-04
You'll have to grab the source for the 8.04 xorg-server and compile under Karmic.

It is unlikely that you will be successful (before mid-2010).

---

### Post by lunaparadox on 2009-11-04
why mid 2010? The ? is how do i compile from the 8.04 server?

---

### Post by Giblet5 on 2009-11-04
> **lunaparadox said:**
> why mid 2010? it worked flawlessly on ubuntu 8.04.

I'm sure, but you're not running 8.04.

You don't intend to run the 8.04 xorg-server on 8.04: the only place where the 8.04 xorg-server will run because the 8.04 xorg-server package was built for, and will only work on, 8.04.

So if you want to run the 8.04 xorg-server on 9.10, then you'll have to port the source code to run on 9.10 and that also includes porting all of the drivers you'll use.

When you're done, the 9.10 GUI software won't work very well because you're running an old busted 8.04 X server that's incompatible with all of the newer applications and features. So you'll have to port the apps that you need as well.

gdm
ubuntu-desktop (big one!)
etc

That would take me about 5 months and I'm good at it. So, 'mid-2010' is about right by my estimate.

:lolflag:

---

### Post by lunaparadox on 2009-11-04
I guess it's mid 2010 lol.
the way to do it is as follows.

go to /etc/apt/sources.list and add deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hardy main restricted universe multiverse to your sources.
then open synaptic and search for xorg highlight it and click on the package menu and force version and choose the 8.04 ver. 

 after that finishes pin xorg so it's not updated from the packages menu. Then install ubuntu-desktop. restart x and ur done. 
Thanks Giblet5

---

### Post by Cenoforums on 2009-11-05
I'm interested in doing something similar. I have an ati card that's working awfully with 9.10, I'm thinking downgrade to the xorg used in 9.04.

Did you experience any problems with stability from the downgrade? any busted applications? Did compiz still worked?

---

### Post by P4man on 2009-11-05
This sounds like a recipe for disaster. I would either try fixing /  changing the ati driver (having trouble with the opensource driver or the binary catalyst?), or stick with ubuntu 8.x. (Or heck change to another distro using an older xorg, or buy a new videocard).

But if you like such experiments, then do try if you want and let us know.

---

### Post by lunaparadox on 2009-11-06
I don't use compiz. still working on getting the second graphics card to work.

---

### Post by Cenoforums on 2009-11-24
Alright, no compiz, but what about the rest? all working?

---

