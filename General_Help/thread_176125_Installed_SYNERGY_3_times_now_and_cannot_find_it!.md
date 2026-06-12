---
title: "Installed SYNERGY 3 times now and cannot find it!"
date: 2006-05-14
forum: General Help
---

### Post by GadgetsGuy on 2006-05-14
Can somebody please help me?!?

I have installed and re-installed, and re-installed again SYNERGY virtual KVM using the Universe repository ... all appears to have worked, however I can not find where it installed it, and more importantly, how to run it.

I am wanting to share my desktop keyboard with my laptop.

thanks!
GG

---

### Post by Sef on 2006-05-14
Hold down alt and press F2.  Then type in synergy in the box

---

### Post by GadgetsGuy on 2006-05-14
Details: There is no default action associated with this location.

---

### Post by GadgetsGuy on 2006-05-15
anybody else who can tell me what I am doing wrong?  

I've never had any problems installing from the Synaptic manager before this

I found synergyc and synergys in /usr/bin but clicking on either one of them does nothing at all

I am at a loss what to do, and having to reach up to use the laptop keyboard is a pain in my a$$  :(

---

### Post by GadgetsGuy on 2006-05-15
ok maybe I am just too dumb to run Ubuntu ... 

I have now even completely un-installed the 4th installation of synergy, and grabbed the rpm from sf ... conveerted it to .deb and installed it 

all seemed to go well

I still cannot find synergy in any menu or any icon that I click to start it

I am now veery frustrated!

/me looking for WinXP install disk ](*,)

---

### Post by Seanuntu on 2006-05-15
I had a similiar experience with Synergy.  I was expecting there to be a GUI much the like the Windows version.  However, there is not a GUI interface for the *nix version.  It needs to be executed from the command line.  Someone else will have to help you with actual commands.

---

### Post by GadgetsGuy on 2006-05-15
Seanuntu (groovy moniker btw)

YOU ARE DA MAN !!!!

I've now got synergy running from terminal!

For anybody else having this problem, here is the solution:
[http://www.linuxjournal.com/article/6393](http://www.linuxjournal.com/article/6393)  :D

Now all I need to do is figure out how to config this to run automatically ... but I am happy I got it running!  They really need to explain to all us linux newbs that it does not have any GUI, and how to run it from terminal.

---

### Post by bauer336 on 2006-05-16
Hi, I had been having the exact same problem. As things are right now, I have synergy installed via the synaptic package manager, here are somethings i still need help with.
#1 How do I edit / make and where do I store then synergy.conf file ?  
I have already tried making a file which is deposited in my home folder, but every time i run the command to get it started, I get an "unknown error" My server machine is a windows xp box which is all configured via the point and click method.. thanks for any help in adcance.

---

### Post by GadgetsGuy on 2006-05-17
[QUOTE=bauer336]Hi, I had been having the exact same problem. As things are right now, I have synergy installed via the synaptic package manager, here are somethings i still need help with.
#1 How do I edit / make and where do I store then synergy.conf file ?  
I have already tried making a file which is deposited in my home folder, but every time i run the command to get it started, I get an "unknown error" My server machine is a windows xp box which is all configured via the point and click method.. thanks for any help in adcance.[/QUOTE]

Bauer336:

The link in my previous post will walk you through making the config file, and what directory it needs to be in.

---

