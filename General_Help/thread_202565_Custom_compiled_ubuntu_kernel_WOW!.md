---
title: "Custom compiled ubuntu kernel: WOW!"
date: 2006-06-23
forum: General Help
---

### Post by patrickfromspain on 2006-06-23
Hi there!!

After having compiled like about 15 kernels (jejejeje) I've just got what I wanted: a fully working kernel for my system. Only for my system.

I have all what I need (cpu scaling; via sata, ide ando sound support, usb, bt848, iptables, etc etc) and "nothing" I don't need (intel speedstep, intel sata, sis ide, saa7134, samba and nfs support, etc...)

The boot speed is now much better: from 1min 37seg to 1min... that is, 37sec less. Not bad eh?

Just wanted to share this with the ubuntu community. If someone is doubting wether compiling a custom kernel is worth the time, I'd say: do it!! :D

---

### Post by loell on 2006-06-23
wow, perhaps you can write a nice howto and links
:p

---

### Post by mlind on 2006-06-23
I'm curious if you built using current Dapper kernel source with Ubuntu patches
applied or did you use source of upsteam kernel?

Did you make oldconfig or used some other defaults?

I've wondered if I should do the same, haven't have any need for it until
I found out that my usb joystic support was fixed on 2.6.17.

---

### Post by patrickfromspain on 2006-06-24
What I did was a sudo apt-get install linux-source. It's a 2.6.15 kernel with ubuntu patches I believe.

To do it, I used oldconfig first, and then, in xconfig, removed the things I didn't need.

---

### Post by lamego on 2006-06-24
What about posting step by step (command line) instructions to save us some google time :p  ?

---

### Post by patrickfromspain on 2006-06-25
Ok, this week I'll post a little howto on what I did

---

### Post by JoWilly on 2006-06-25
[quote=loell]wow, perhaps you can write a nice howto and links
:p[/quote]

There are many howtos already... just search for "howto kernel compile".

---

### Post by dcstar on 2006-06-26
[QUOTE=JoWilly]There are many howtos already... just search for "howto kernel compile".[/QUOTE]
Exactly, are people too lazy to have a look in the "Tips and Tricks" forum?:

[http://ubuntuforums.org/forumdisplay.php?f=100](http://ubuntuforums.org/forumdisplay.php?f=100)

---

### Post by loell on 2006-06-26
[QUOTE=dcstar]Exactly, are people too lazy to have a look in the "Tips and Tricks" forum?:

[http://ubuntuforums.org/forumdisplay.php?f=100](http://ubuntuforums.org/forumdisplay.php?f=100)[/QUOTE]

maybe they are or we are, those threads in the how to's gets bulky with countless pages from the first original post, having to ask it from the thread starter how he does it in his own interpretation is not compulsory though
thanks for the link anyway..

---

