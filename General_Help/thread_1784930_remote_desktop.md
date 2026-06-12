---
title: "remote desktop"
date: 2011-06-17
forum: General Help
---

### Post by TwistedName on 2011-06-17
good day, i have just installed a copy of Lubuntu on an old machine and would like to remo....ive just spotted a dead pixel on my screen :(

...and would like to remote desktop to it. it comes with nothing installed by default. all i realyl want to know is. how to i get the "remote desktop preferences" that are in the ubuntu menu -> system -> preferences -> remote...

mainly i want to know what they are called in synaptic. i hope this makes some kind of sense. 

ive installed a few rdp things, but i still cannot connect to it. im trying to use ubuntu 10.10? to connect to lubuntu. should be simples right.

---

### Post by DirtyPC on 2011-06-17
I don't know personally, but try searching the forums.

---

### Post by pricetech on 2011-06-17
Use SSH for that.  Search for "opensshserver" in Synaptic (without quotes of course)

If you need a GUI, download NX from nomachine.com.  You'll need client, node, server for your Linux box and they even have a Windows client in case you're interested.

Works for me.

---

### Post by TwistedName on 2011-06-17
thank you very much, i shall give it a try in the morning when im slighrty less intoxicated, goood night

---

### Post by crispy_420 on 2011-06-18
+1 NX Server/Client

I use it all the time and I believe it is secure (ssh) as a bonus.

---

### Post by majedaly on 2011-11-23
Just had the same issue. You can easily install vino.
Desktop sharing is composed of 2 sides, server side , which is the machine you want to connect to, and client side, which is the machine you want to connect FROM.
The server side is called vino, you can install by typing
sudo apt-get install vino

---

### Post by cybergalvez on 2011-11-23
I like x2go

---

