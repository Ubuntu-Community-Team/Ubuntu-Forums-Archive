---
title: "4th gen. iPod nano - cpu sees songs/ipod not seeing them as music"
date: 2009-09-26
forum: General Help
---

### Post by smartsmokey on 2009-09-26
i had the older iPod shuffle going fine with Hardy (8.04)...i think i had formatted it - either HIPO or AMarok or Rythmbox had qeued me with a "format?" question, and it formatted etc. Well I bought this new iPod, the 4th generation nano - and using Amarok and Rythmbox and HIPO and the multiple threads about this on the net, I can NOT et the iPod to recognize the files as music - it's IN the iPod - when disconnected from computer it reads it as about 600mb of "other." When I connect to the computer I can see the songs I've loaded onto it - and they're not "other," they're actual songs. I COULD use the Windozexp OS iinstead to connect to itunes and do it legit...but when I set up the dual boot or whatever you'd call it (I have a choice of either ubuntu or windows xp in the grub) i have it so that from ubuntu i can see "5.6gb media" which is the windows os and that hard drive partition - but when I'm in windoze I can't see any of the ubuntu stuff. Might make another post about that](*,):cry:

---

### Post by smartsmokey on 2009-09-26
okay i open GTKPOD and get this pop up -
"Could not open "(null)" for reading extended info.
Extended info will not be used."
what the heck? SO i hit "ok" and gtkpod is open, shows the ipod, but seems to have 5 entries for "new ipod" - like one for every time i've connected it? what's going on here? I'm going to keep tinkering with GTKPOD and keep and on if any other brave souls who might have done this or know how to do it

EDIT:
just got this, not sure how i got there - 
Error initialising iPod: Couldn't find the iPod firewire ID
Error initialising iPod: Problem creating iPod directory or file: '/media/ADMINISTRAT/iPod_Control'.

---

### Post by ppirilla on 2009-09-26
iPods (except for the shuffle) have a separate way of storing music data from "other data," i.e. using the iPod as a memory stick.

I believe that gtkpod is your best choice for transferring music for the iPod to actually play.


On your other comment, there is software out there to let Windows look at ext2/3 partitons.  I used it in the past for an ext2 external hard drive, and it worked well.  I don't have the link on hand, but if you want to go that route, search "windows ext2" and it should come up.

---

### Post by smartsmokey on 2009-09-26
okay i was closing down gtkpod to see if i actually did anything, and got this - The following 65 dangling tracks do not have files on PC. 
Press OK to remove them, CANCEL to leave them. as is
and then it shows the songs below it. What is this?

---

### Post by smartsmokey on 2009-09-26
> **ppirilla said:**
> iPods (except for the shuffle) have a separate way of storing music data from "other data," i.e. using the iPod as a memory stick.

I believe that gtkpod is your best choice for transferring music for the iPod to actually play.


On your other comment, there is software out there to let Windows look at ext2/3 partitons.  I used it in the past for an ext2 external hard drive, and it worked well.  I don't have the link on hand, but if you want to go that route, search "windows ext2" and it should come up.

thank you ppirilla!

---

### Post by speedwell68 on 2009-09-26
You could try Songbird with the iPod support addon.  You can get the latest Songbird from GetDeb.

---

### Post by smartsmokey on 2009-09-26
> **speedwell68 said:**
> You could try Songbird with the iPod support addon.  You can get the latest Songbird from GetDeb.

i think i might just check it out. godspeed speedwell!

---

### Post by smartsmokey on 2009-09-26
okay i ended up botting into Windows XP and downloading itunes and syncing. The songs that I had put on with gtkpod/amarok/rythmbox which weren't being recognized by the ipod once disconnected suddenly became actually "active." Although, I don't know what to do about cover art. And each song, in itunes, show an "explicit" warning next to it - even though they're like Beatles songs and Crosby Stills Nash

---

