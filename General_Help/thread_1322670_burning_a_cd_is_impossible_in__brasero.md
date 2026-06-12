---
title: "burning a cd is impossible in  brasero"
date: 2009-11-11
forum: General Help
---

### Post by dyyyy on 2009-11-11
hi, i found on the web, that i'm not the only one having this problem..
first ubuntu couldn't detect a blank CD, so i had to install volume manager, which strangly removed Brasero, i downloaded it again, 
but now sometimes it detects the blank CD, sometimes it don't
and when it does i get an error when burning a CD.
so if anyone can help me, thank you
i'm using ubuntu 9.10

---

### Post by Plumtreed on 2009-11-11
I don't have an answer to the Brasero question but I solved my problem by downloading K3b from the Synaptic repository. I needed to burn a CD and didn't have time to 'ask questions'.

Brasero worked in 9.04 but, for me at least, it failed in 9.10.

---

### Post by dyyyy on 2009-11-12
thx,
but k3b seems like it;s for KDE does it work on ubuntu without any problems?

---

### Post by jmszr on 2009-11-12
dyyyy,

k3b works very well in Ubuntu - it's the burning app of choice for a lot of people. Installing k3b also installs the libs that k3b needs to function, there are no problems.

---

### Post by kennedyjch on 2009-11-14
I too have problem burning data CDs on my Philips CD/DVD drive with Brasero. Would die after writing the data with HUP and error code 254...

Installed K3B and it works like a charm :p

---

### Post by garvinrick4 on 2009-11-14
Brasero worked fine for me and always has I do believe I turned down the speed
of the burn when burning to make sure I get good image. If I am right I think it
is defaulted to 16x and I use 8x. That sounds like it. I understand the slower the burn
the better chance of getting nice Live CD out of .iso image. 
  Just a thought.

---

### Post by kennedyjch on 2009-11-14
Indeed. That is what I was doing until I upgraded to 9.10 and then Brasero would only allow me to select between "Max" and "16x". However, when I installed K3B, it gave he a whole host of different speeds that Brasero never offered. So until Brasero is definitively fixed so that my PC is no longer a "coaster factory", I will stick with K3B.

---

### Post by dyyyy on 2009-11-14
hi i installed k3b,
but the problem is that it doesn't convert mp3 files to audio :(:(
any solution for this?

---

### Post by dyyyy on 2009-11-16
ok i got the mp32ogg script
but unfortunatly k3b doesn't work
it gives me an error when i'm burning the CD,
smthg... u can try with TAO...(sorry i'm not on my linux pc right now :P)
and when i try with TAO it gives the error ...u can try with DAO...

---

### Post by XubuRoxMySox on 2009-11-16
MP3s won't be recognized without some extra non-free software. Go [here]("https://help.ubuntu.com/community/Medibuntu") and follow the instructions to add the Medibuntu repository and the codecs and such that you need for MP3's to play.

Also make sure you have ubuntu-restricted-extras installed (check in Synaptic).

+1 to K3b, by the way. It rawks compared to Brasero!

-Robin

---

### Post by missmoondog on 2009-11-16
i've been trying to figure out why that piece of crap brasero is the default burning app in ubuntu since day one.

it doesn't convert files on the fly, which more than doubles the time it takes to burn a cd and half the time, simply doesn't work.

when installing k3b, simply add the "extracodecs" package, which is right under k3b in synaptic's list, when searching for it.

---

