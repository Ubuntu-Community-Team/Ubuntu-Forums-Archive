---
title: "libdvdcss2 limitation Star Wars EP. III?"
date: 2006-04-09
forum: General Help
---

### Post by racoq on 2006-04-09
Hello

I have my shining new Linux system running and "kicking". However since i've installed it for testing in my girlfriend's laptop (for having the experience to later build a server on other machine using Ubuntu server mode), i've installed all the major aplication and all went OK. After that i've tride to install all the multimedia apps, and saw the official Restricted Formar Ubuntu Wiki. So i've decided to add support for  dvd playback on the laptop. I've installed libdvdcss2, xine-libs, and xine-ui, for doing the job.

So.. For testing i've used The DVD that i've buyed Of Star Wars Ep. III, The Revenge of The Sith. However Xine, or even Totem refused to play it saying it was encrypted (and libdvdcss2 is well installed). Since that i've tryed the DVD 2 of star Wars ,and other DVD films like The Gladiator and they've all played.

What i think is the reason, is that for playing DVD's on Xine, the Vob's have to be decrypted for playback. And Since i know friends of mine that  tried Ripping my dvd in Windows, and they couldn't make it. Is it possible that The Star Wars EP.III DVD encription, is to ahead for  libdvdcss2 to handle?

Just another question my Laptop as an ATI radeon, and the quality is worst on xine than playing power DVD in windows, is it possible to improve its quality by installing any driver for the graphic card of the laptop, or some other procedure?

---

### Post by racoq on 2006-04-09
Just for the Record i have an ATI Mobility Radeon 9700 (64 MB), and i've tested the DVD U2, The best of 1990-2000, and the DVD isn't even detected by Ubuntu (He loops trying to read the DVD, but it never reads it.,). 

The Error that the xine shows decoding DVD Star Wars EP III, is in atachment 

Any Idea?

---

### Post by racoq on 2006-04-09
Hello, Finally i've managed to do the folowing

I've edited the /etc/apt/sources.list , and added the folowing lines:

deb [http://hpisi.nerim.net/](http://hpisi.nerim.net/) stable main
deb [http://www.interq.or.jp/libra/oohara/debian-unofficial/](http://www.interq.or.jp/libra/oohara/debian-unofficial/) ./
deb [http://download.videolan.org/pub/videolan/debian](http://download.videolan.org/pub/videolan/debian) woody main

after that i've updated all the updating mirrors listed in sources.list, by doing:

apt-get update

After that the update manager appeared in the taskbar, saying that there where new updates.

I've clicked there and a new version  libdvdcss2 appeared for update, and Voilá, now i can see all teh DVD's Including Star Wars EP.3. Probably the  libdvdcss2, wasn't well installed.

Hope someone learn from my experience.

---

### Post by nzruss on 2006-04-09
[QUOTE=racoq]
Hope someone learn from my experience.[/QUOTE]

I'm sure they will, its a good tip

nzruss

---

### Post by jms830 on 2006-04-24
could you tell me specifically which packages you installed from those sources for dvd because I'm a little hesitant to install more than I have to from the sources? thanks!

Edit: sorry, I missed you wrote that you just installed the new libdvdcss2. for some reason it does not show up after apt-get update. also, I get a 404 error for the first source you listed (nerim). Maybe this is why?

---

### Post by Hairy_Palms on 2006-04-24
just download and install [http://download.videolan.org/pub/libdvdcss/1.2.9/deb/libdvdcss2_1.2.9-1_i386.deb](http://download.videolan.org/pub/libdvdcss/1.2.9/deb/libdvdcss2_1.2.9-1_i386.deb)
its the latest version use the command sudo dpkg -i libdvdcss2_1.2.9-1_i386.deb

---

