---
title: "wiped my /usr/lib folder"
date: 2009-11-17
forum: General Help
---

### Post by OleR on 2009-11-17
Hey everyone,

I think I just messed up the work of days using a stupid mv command. I know there is no simple way to reverse this, just want to check twice if there is any smart way to repair in my specific case before I start all over again. 

I wanted to move a library that I had compiled to the /usr/lib folder, but accidentally entered

sudo mv libmylib.a /usr/lib/*

which of course wiped my entire /usr/lib folder. Great. I am a little bit surprised my Ubuntu is still running okay, but of course I cannot compile anything at the moment and I guess all kinds of other stuff is broken too. So ist there anyway to reinstall all these libs that are gone without wiping the hard disk and reinstalling ubuntu from scratch and all the libs I had installed?

I should maybe say that I am running Ubuntu in a Virtual Box in a Snow Leopard host system, but of course have not made any backup points...

---

### Post by blueridgedog on 2009-11-17
You could install a new guest os, then copy the /usr/lib from it to the one you have.  You will not get everything, but it is a shot.

I would just put it down to two great lessons learned and do the re-install.

---

