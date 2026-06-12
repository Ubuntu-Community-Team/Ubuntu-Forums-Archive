---
title: "Copy of GRUB Menu.lst for Ubuntu 9.10"
date: 2010-05-01
forum: General Help
---

### Post by stevepaul on 2010-05-01
This may seem like a strange request but please bear with me (as I'm a newbie)...

Recently I installed (then unistalled) Startup Manager (SM) because I wanted to have a play with changing my *[COLOR="Blue"]Splash screen[/COLOR]* at startup ...

Subsequently when rebooting into Ubuntu I got an *[COLOR="Blue"]'Undefined Video Mode Number:307'[/COLOR]* error ...

After a few hours *[COLOR="blue"]Googling[/COLOR]* (and *[COLOR="blue"]Yahooing[/COLOR]* and *[COLOR="blue"]Binging[/COLOR]*) I managed to resolve the issue ...

However as I didn't know I was going to encounter this error (or what it was going to affect) I hadn't backed anything up (I know - lol)

As I said I've managed to resolve the issue by editing the *[COLOR="Blue"]Grub[/COLOR]* *[COLOR="blue"]Menu.lst[/COLOR]* but what I'd like to see is what the *[COLOR="blue"]Grub Menu.lst[/COLOR]* would have looked like before I installed SM...

What I suspect is that SM added a line to the *[COLOR="Blue"]Menu.lst[/COLOR]* for the *[COLOR="blue"]'Splash Screen'[/COLOR]* and it's this that caused the problem ...

Anyway what I'd like is for someone to post a copy of their *[COLOR="blue"]Menu.lst[/COLOR]* so I can compare it to the one I have ...

In order to get something that is compatible I have the latest version of 9.10 installed with a Vista *[COLOR="blue"]'dual boot'[/COLOR]* so when I first *[COLOR="blue"]'boot'[/COLOR]* I am offered 3 versions of Ubuntu and Vista (if you've got XP or 7) that will do ...

Hope this makes some kind of sense ;-)

---

### Post by mister_playboy on 2010-05-01
Ubuntu keeps a copy of the last version of menu.lst (called menu.lst~) whenever you make changes.  You can find it in /boot/grub.

I doubt looking at anyone else's menu.lst would be helpful...

---

### Post by stevepaul on 2010-05-01
I know that ...

The reason I'd like to see someone else's *[COLOR="blue"]Menu.lst[/COLOR]* is to see if my assumptions are correct ...

I'm assuming that SM added the following to my Menu.lst ...

*[COLOR="Blue"]'ro quiet splash   vga=775'[/COLOR]*

The 775 when converted equates to 307 which is not defined, hence the error message ...

Seeing some else's *[COLOR="blue"]Menu.lst[/COLOR]* would confirm if my suspicions are correct ...

---

### Post by oldfred on 2010-05-01
Your vga= is not a standard entry unless you need it. 

You can try booting without it by.
Press e on getting the GRUB bootloader.
Using arrow keys navigate to and delete the vga=775
Press Ctrl and X to boot

If that works then you can remove it from menu.lst. 

Grub2 obsoletes the vga modes and uses something like this:
set gfxpayload=800x600x16, 800x600

This site has a cross ref table nearer the bottom of the page:
[http://wiki.archlinux.org/index.php/Gensplash](http://wiki.archlinux.org/index.php/Gensplash)

---

### Post by stevepaul on 2010-05-01
@oldfred

Tbh I've messed about with this quite a bit ...

From changing the *[COLOR="Blue"]vg[/COLOR]*a to actually commenting out the lines that have the *[COLOR="blue"]vga[/COLOR]* content and everything I've done has worked OK ...

Again, the reason I want to look at a *[COLOR="blue"]Menu.lst[/COLOR]* from a *[COLOR="blue"]9.10 Grub[/COLOR]* is to see exactly what it was that the *[COLOR="blue"]Startup Manager[/COLOR]* added as there is more than one entry against different things ...

I'm afraid it's the detective in me, I like to understand how things work and why...

For instance the lines that (apparently) have been added contain certain *[COLOR="blue"]'syntax'[/COLOR]* and it's nice to know what they actually do ..

However thanks for your contribution

---

