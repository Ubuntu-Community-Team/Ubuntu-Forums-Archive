---
title: "Using a thumb drive for extra ram?"
date: 2011-05-01
forum: General Help
---

### Post by webcabbie on 2011-05-01
So i saw a thread somewhere about using a thumb drive to make extra ram for your pc. This was of course on a windows pc. I was wondering if this works on Ubuntu also and if it is really worth it?

Also if you have 4 USB ports could you put in 4 usb thumb drives and have a fantastic amount of ram?

---

### Post by 5149.5 on 2011-05-01
That would be very slow ram.  Leave this kind of thinking for the mental giants in Washington.

---

### Post by tgm4883 on 2011-05-01
> **webcabbie said:**
> So i saw a thread somewhere about using a thumb drive to make extra ram for your pc. This was of course on a windows pc. I was wondering if this works on Ubuntu also and if it is really worth it?

Also if you have 4 USB ports could you put in 4 usb thumb drives and have a fantastic amount of ram?

It's not using the thumbdrive as RAM, it's using it as swap. The feature is built into Windows 7 and is called [Readyboost]("http://en.wikipedia.org/wiki/ReadyBoost").

A quick search turned up this [How to: ReadyBoost with Ubuntu Linux]("http://ubuntuforums.org/showthread.php?t=395435")

---

### Post by antaios256 on 2011-05-01
> **webcabbie said:**
> So i saw a thread somewhere about using a thumb drive to make extra ram for your pc. This was of course on a windows pc. I was wondering if this works on Ubuntu also and if it is really worth it?

Also if you have 4 USB ports could you put in 4 usb thumb drives and have a fantastic amount of ram?


as for windows i know this will only affect loaded programs post boot such as files from word and excell however the extra channels needed for video ram are not practical in readyboost and therefore not used. and thus makes it not really worth it.

as for ubuntu i have no idea

---

### Post by oldos2er on 2011-05-01
> **webcabbie said:**
> So i saw a thread somewhere about using a thumb drive to make extra ram for your pc. This was of course on a windows pc. I was wondering if this works on Ubuntu also and if it is really worth it?

Also if you have 4 USB ports could you put in 4 usb thumb drives and have a fantastic amount of ram?

Fantastically slow. Much better to max out the real RAM on your motherboard.

---

### Post by webcabbie on 2011-05-01
My reasoning for doing it are kinda weird. 

I have just installed virtualbox to run xp on my my ubuntu machine. The program I run on virtualbox xp needs like a gig of ram to run. 

My box only has 2gb installed so even allocating half of my installed ram to the virtualbox it still kinda runs slow. So maybe see if this works in XP and install it in Virtualbox xp allocate a bit less ram from the box itself to the virtualbox and then hope the program I am running will use the thumb drive ram?

When I am done with this I plan to divide by 0

---

### Post by 5149.5 on 2011-05-01
Dividing by zero will work better. :p

---

### Post by snowpine on 2011-05-01
It would be faster to create a swap partition on your internal hard drive than on your flash drive. (This is the default setting for the Ubuntu installer.)

---

