---
title: "Gnome 2.14 Requirements"
date: 2006-04-27
forum: General Help
---

### Post by racoq on 2006-04-27
Has anyone tested gnome 2.14? I've eard that it runs better on old systems that previous versions. So what i ask here is, what are the minimal hardware requirements for runing smooth enough, this latest version, in terms of CPU (AMD or Intel), graphic card memory, and ram memory.

I'm looking here for user experience on this subject, not  gnome official requirements ;)

---

### Post by PriceChild on 2006-04-27
You're not thinking of putting it onto your current Breezy are you? I don't think that'll work at all :s

Dapper includes it, why not give it a quick spin?

---

### Post by az on 2006-04-27
Dapper runs okay on pIII 400 with 128 megs of ram.

Anything better than that gets better and better.  Anything less than 300Mhz or 128 megs of ram is painful, but possible.

I do most of my work and browsing on a pII 600 with 394 megs of ram.  It's fast enough - faster than windows XP would be.

---

### Post by racoq on 2006-04-27
I have a AMD k6-III 450 MHZ, S3 savage 16MB, and 128 MB ram! So what you guys say is  that it will run well on dapper with gnome 2.14. Right?

---

### Post by az on 2006-04-27
[QUOTE=racoq]I have a AMD k6-III 450 MHZ, S3 savage 16MB, and 128 MB ram! So what you guys say is  that it will run well on dapper with gnome 2.14. Right?[/QUOTE]

A k6-III has a very small cache - like a Celeron in comparison to a pentium.  It will be slow.  You would bebefit from more ram, even 64 megs more.

---

### Post by Jagot on 2006-04-27
[QUOTE=racoq]I have a AMD k6-III 450 MHZ, S3 savage 16MB, and 128 MB ram! So what you guys say is  that it will run well on dapper with gnome 2.14. Right?[/QUOTE]

It should run but not fantastically.  If you can, boost your RAM a bit.

---

### Post by racoq on 2006-04-27
So what i understand the more memory ram, the more smoothly gnome will run. So my graphic card is enough?

---

### Post by Jagot on 2006-04-27
Generally with Linux the more RAM the better.  Linux utilises RAM more effectively than Windows so you don't necessarily need a a stunningly fast processor for it to be able to run well.  

You won't be able to do anything stellar with that graphics card but it should be able to perform normal tasks fine.

---

### Post by racoq on 2006-04-27
Thanks all, for the tip. I will try gnome first, and if it doesn't run as i'm expecting i will install XFCE. Meanwhile, if i don't like XFCE, i will try to find more ddr ram for my PC.

---

### Post by az on 2006-04-27
[QUOTE=racoq]Thanks all, for the tip. I will try gnome first, and if it doesn't run as i'm expecting i will install XFCE. Meanwhile, if i don't like XFCE, i will try to find more ddr ram for my PC.[/QUOTE]
Sure, your graphics card is fine, although you will not be able to do anything that requires hardware acceleration - there is no RDI for S3.

XFCE will not be a lot faster than gnome on an amd k6-II.  Try icewm or fluxbox.  (make sure you install icewm along with the menu package

sudo apt-get install icewm menu)

---

