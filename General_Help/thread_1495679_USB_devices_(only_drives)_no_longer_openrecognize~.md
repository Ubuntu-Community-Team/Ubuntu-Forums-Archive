---
title: "USB devices (only drives) no longer open/recognize~ Project due today~ Help!?"
date: 2010-05-28
forum: General Help
---

### Post by Rasa1111 on 2010-05-28
Hi all, 

 Just as my luck would have it, lol

Ive a project due this afternoon for the observatory, 
and all I needed to do was plug in my external hard drive and work on a banner in GIMP~

 However~ Now suddenly none of my external media will open~
Not my external HD, not my smaller flash drives.. none of it. 

USB devices such as mice and keyboards work fine though. 

 I have tested my external on my other PC with 9.10/Karmic~
and it opens normally, like it always does. 
(however, that PC is not online and this box has all the tools I need)

 So I know it is not the drive itself.. 
but something that went awry in 10/04/Lucid. 

 Question being~
What could it be? 
and is there something I can do to correct it?
rather~* what* can I do to correct it? 

 It is now 10:28 am here~ and I really should have this banner finished and to the observatory by about 5 p.m. today. 

So there are some hours to get it worked out, 
But can any of you help a brother out? 

 Ive not had this problem, or any kind like it in Ubuntu before..
and my searches turn up rather fruitless... :(

Any insight welcome, and greatly appreciated. 

(p.s.. I can get you free time on the 30" scope if you can help!.. and a tour & all. ) lol
Thanks, Rasa
.

---

### Post by Rasa1111 on 2010-05-28
i really am not one to bump my own threads..
but in this case i kind of have to. lol :(
im sorry.

any of you know what could be going on here? :/

---

### Post by dino99 on 2010-05-28
sudo update-pciids && update-usbids
sudo apt-get update
sudo apt-get install -f
sudo dpkg --configure -a

into synaptic: remove/purge (right-click) then reinstall pmount & usbmount

you can install mountmanager to deal with partitions and devices (tweak it as you need: system admin mountmanager)

---

### Post by Rasa1111 on 2010-05-28
> **dino99 said:**
> sudo update-pciids && update-usbids
sudo apt-get update
sudo apt-get install -f
sudo dpkg --configure -a

into synaptic: remove/purge (right-click) then reinstall pmount & usbmount

you can install mountmanager to deal with partitions and devices (tweak it as you need: system admin mountmanager)

Dino my man~
 Thank you! :mrgreen:

 My Seagate external is now accessible and open! 
You are beautiful my friend! :)

 Strange though~ 
when I went into synaptic to remove and reinstall pmount & usbmount,  Neither of them were even installed!??  lol

 is that normal?

 Im positive Ive removed nothing,
 nor added any new programs in a couple weeks, 
so im not sure how they would have gotten removed?
If indeed they did. 

 anyway, after the commands in terminal and installing them..
I am back in business my bro. Praises to you Dino.
You saved me. :)
  <3

If youre ever up for some viewing of the Universe with big telescopes, hit me up!  lol
Thanks man. :)

---

### Post by Rasa1111 on 2010-05-29
Well,

 Major 'DOH!' on my part! lol

The culprit was~

 The night before, [ I completely forgot about it ]
I had found an old floppy disk and stuck it in to see what was on it~
I then totally forgot I even put it in there, and never even checked what was on it~

 So the next day, [for whatever reason] the floppy disk in the drive was preventing anything else from being read. 

So there was no real issue after all, 
and turns out I didnt even need to install pmount and usbmount. lol
after i removed the disk, everything worked proper again! 

 Man,  I thought Ubuntu had a 'beef' with me. lol
but it was just my own DUHness. 
go figure. :lol:

Solved.
 Thanks again Dino!

---

