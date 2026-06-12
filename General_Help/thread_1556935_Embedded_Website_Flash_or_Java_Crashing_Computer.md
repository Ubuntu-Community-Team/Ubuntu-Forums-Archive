---
title: "Embedded Website Flash or Java Crashing Computer"
date: 2010-08-20
forum: General Help
---

### Post by cro_409 on 2010-08-20
Hi guys,
When using the internet or internet provided programs (ie, Google Earth) I frequently crash. I decided to run some controlled testing, and realized it is only on sites that use some kind of video on it. Not movies or clips but more like advertisement or embedded video that plays as soon as you enter the website. Whether it is Flash or Java I haven't been able to determine, but on those sites or programs it crashes 100% of the time within 10 seconds of starting. 

The screen goes dark gray with a blinking white cursor in the very upper left hand of the screen. It then goes black, as if it went into hibernate or sleep mode, but pressing the keyboard, moving the mouse, or pressing the power button on the tower do not wake it up. 

The only solution is to hold down the towers power button until it turns off, and then press it again until it boots up. After that I do not have any problems until I run into a site that uses these embedded video players.  

I don't believe it was like this several days ago when I first installed 9.10, but to my recollection it happened after an upgrade. I then upgraded via the Update Manager with the hopes of it being solved, and have since had no other issues but this same one.

I am hoping someone can give me a fix. Maybe I have an outdated or corrupt codec or maybe I am missing some codecs or video software. I have no available updates on the Update Manager. I am almost certain it is Flash or Java, or maybe both. Google Earth and Dodge.com caused crashes everytime almost immediately. Maybe someone could check to see what they use to narrow it down, because I can't. 

I tried doing the tests randomly, and once right after restarting, and once after no restarts for several hours after being on only text sites, and both caused immediate crashes.

Thanks!

Ubuntu 10.04

---

### Post by mastablasta on 2010-08-20
Do you use Adobe Flash and Sun Java or their open source "alternatives"?

---

### Post by cro_409 on 2010-08-20
mastablasta, you are my new hero.
Checked my software for Sun Java, noticed I had nothing, went into Synaptic and downloaded a Sun Java plug in for Mozilla and all is perfect. All my "test websites" work perfect with no crashes!

Thank you so much!!

Case Closed,
and i can go back to researching for my next car.

---

### Post by lovinglinux on 2010-08-20
Also use [NoScript]("https://addons.mozilla.org/en-US/firefox/addon/722/") and [AdBlock Plus]("https://addons.mozilla.org/en-US/firefox/addon/1865/") so you don't load those flash ads. [Flashblock](https://addons.mozilla.org/en-US/firefox/addon/433/) can also block flash, but NoScript block other dangerous stuff too.

---

