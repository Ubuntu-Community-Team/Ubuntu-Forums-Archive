---
title: "Mediatomb -&gt; Content showing multiple times, not playing"
date: 2011-07-25
forum: General Help
---

### Post by goodvikings on 2011-07-25
Hey everyone

I have a problem with Mediatomb. I'm about to ask over at the mediatomb forums but I fear that no one actually uses those so I won't get an answer there....

I have Mediatomb running on Ubuntu Server 8.04 for use with a PS3. The problem is that some of the content is getting displayed multiple times.

For instance, if on the PS3 I navigate to Audio -> Albums -> <some album>, each track gets listed over and over again, continually being discovered by the server, but none will actually play. They also show up multiple times if I use the web UI, and its not for all albums, just a few.

I've tried deleting the sqlite db in /var/lib/mediatomb a few times, it just does it over again to the same albums.

Any ideas? Any suggestions appreciated.

It's quite distressing, I can't get my Pink Floyd stuff to play :(

---

### Post by goodvikings on 2011-07-25
bumpin

---

### Post by Gyokuro on 2011-07-25
stop mediatomb via: 
sudo /etc/init.d/mediatomb stop

delete the database in 

/var/lib/mediatomb

and restart mediatomb afterwards via: 

sudo /etc/init.d/mediatomb start

but I have to admit that I switched to PS3 MediaServer long time ago.

---

### Post by goodvikings on 2011-07-25
Uh yeah, I mentioned I tried that. Anything other ideas?

---

### Post by goodvikings on 2011-07-26
bumpin

---

### Post by goodvikings on 2011-07-27
they see me bumpin

---

### Post by goodvikings on 2011-07-28
they hatin :(

---

