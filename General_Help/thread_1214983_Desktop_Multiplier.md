---
title: "Desktop Multiplier"
date: 2009-07-16
forum: General Help
---

### Post by bryce123 on 2009-07-16
Hi guys,
I am currently building a media production workstation based entirely on open source software. One PC should be used for multiple seats via a desktop multiplier.
I did not find any open source packages that provide this functionality. Since this should be workstations for "light" video editing, sound/music creation and so on, the classical server/terminal solutions wont work.
Do you have any ideas how to achieve this with open source software?
Thanks

---

### Post by bryce123 on 2010-04-02
*push*

---

### Post by NightwishFan on 2010-04-02
I am not sure what a desktop multiplier is. ;)

---

### Post by bryce123 on 2010-04-02
This:
[http://www2.userful.com/products/userful-multiplier](http://www2.userful.com/products/userful-multiplier)

---

### Post by NightwishFan on 2010-04-02
It might be possible with some sort of virtualization solution. I am not the one to ask though, obviously.
[http://www.ubuntu.com/products/whatisubuntu/serveredition/technologies/virtualization](http://www.ubuntu.com/products/whatisubuntu/serveredition/technologies/virtualization)

EDIT: Virtualization coupled with the realtime kernel used in Ubuntu Studio might lead to performance problems (not sure) I would use the generic kernel if you decide to go this route.

The only other thing I can think of is VNC or SSH into a machine, Linux is designed to be multiuser.

---

### Post by Calash on 2010-04-02
When you say multiple seats, do you mean full computers or some kind of dumb terminal?

You can do many different things with Linux to Linux, from remote control of entire desktops to using SSH to shell out Xserv windows.  It will help to know the type of hardware you are working with.

---

### Post by bryce123 on 2010-04-02
My reasoning is this: I want one powerful desktop computer instead of multiple expensive thin clients or old pcs, where people can work at the same time on multiple seats. Since this work involves multimedia work, "normal" terminal server stuff wont cut it anyways.

---

### Post by Calash on 2010-04-02
Just so I am sure I understand...you are talking about a single computer with several Monitors, Keyboards, and Mice connected.  Each station would be a separate environment but all run by the same computer.

Is that accurate?

---

### Post by bryce123 on 2010-04-03
Yes, that is correct.

---

### Post by sir_nasty on 2010-05-03
it was mentioned earlier in this thread but userful will do what you want.  I use it currently in 9.10 and I think I might have just modified their installer enough to get it to work in 10.04..... I'll know more tomorrow.... it's free for a 2 seat setup.

---

### Post by AndresM on 2010-09-20
> **Calash said:**
> Just so I am sure I understand...you are talking about a single computer with several Monitors, Keyboards, and Mice connected.  Each station would be a separate environment but all run by the same computer.

Is that accurate?
I'm interested in this as well! 

I heard it was just a question of plugging in an extra screen, an extra keyboard and an extra mouse... I guess not all distros can do that...

---

