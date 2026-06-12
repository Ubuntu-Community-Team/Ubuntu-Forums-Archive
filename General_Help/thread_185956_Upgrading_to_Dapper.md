---
title: "Upgrading to Dapper"
date: 2006-06-01
forum: General Help
---

### Post by InsanePenguin08 on 2006-06-01
I upgraded to Dapper last night, before the official release, but I ran into a huge problem that kept me up until 2 in the morning.  And I had exams today. I ended up fixing it, but I'm back in Breezy and I'm not sure what exactly I did.

Anyways, I'm sure you've all heard about the Xserver and GDM errors that seemed to be popping up, and from what I can tell, Dapper doesn't support ATI Radeon cards under X8500.  I have an ATI Radeon X850 Pro graphics card, and I really would like to upgrade to Dapper, but am I going to have this error again?  And if I do, has there been a way to solve it?

I'd tried changing the driver in sudo nano /etc/X11/xorg.conf to 'vesa' and 'radeon' and a bunch of others.  Didn't help.  I also ran sudo dpkg-reconfigure gdm and sudo dpkg-reconfigure xserver-xorg, which didn't help either.

Thanks in advance, I apologize for the long-winded post!

---

### Post by Ramses de Norre on 2006-06-01
What exactely did happen? I run an ati x600 with fglrx and the upgrade went fine.. (I did had problems with X crashing when I installed ubuntu the first time, using fglrx solved this).
A little more info about the errors you receive etc could be useful.

---

### Post by bvanaerde on 2006-06-01
Bah, I can never remember which card is newer and which is older. Why can't they just use ascending numbers :)

Anyway, I've got a ATI Radeon 9700 on my laptop, and everything works fine.
Isn't your graphics card newer than mine? So normally that shouldn't be the problem...

---

