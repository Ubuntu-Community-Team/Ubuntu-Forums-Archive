---
title: "Jack and Ardour"
date: 2006-04-04
forum: General Help
---

### Post by hglb on 2006-04-04
Another newbie here. I need a music studio like frootloops or acidpro. i just installed kubuntu last week so i'm lost. I tried Downloading Ardour but it can't connect to jack. so I ran jack in the terminal and I got this message:

This is jack 3.1.1 (C)2004 Arne Zellentin <zarne@users.sf.net>
Access of CD device /dev/cdrom resulted in error: Input/output error

Help Please!](*,)    

                                         Thank You - LB

---

### Post by hglb on 2006-04-05
well maybe when linux can work for people like me ill switch. but im lost here so im gonna have to go back to windows. sorry guys.

---

### Post by Paulo Wageck on 2006-04-07
try some time later....

remember... leave the darkside. 
may the force be with you!


i am ready... windows free for 6 months...

---

### Post by Iandefor on 2006-04-08
For some reason, there are two packages (Linux parlance for either an application, a library that lets a program run, some piece of core system software, or even some combination of the above) that use the name jack. When you install the first one, it uses the command 'jack', but it's not the one you want. It's a CD ripper. What you want is the other one- which, when you install it, uses the command jackd. You should have it installed already. Try the command ```
jackd -d alsa
``` and see if ardour runs then. If it doesn't, run the above command and post what it outputs.

  	@Paulo Wageck:

Let's try to keep our responses constructively supportive, eh?

---

### Post by Gibran on 2007-05-27
Well, this did it for me, Iandefor, thanks!

---

