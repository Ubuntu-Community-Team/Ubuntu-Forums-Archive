---
title: "Ubuntu Keep Changes Permissions!"
date: 2011-10-24
forum: General Help
---

### Post by Spice Girls on 2011-10-24
Lately, when I put in my memory card, USB drives, Ubuntu keeps changing permissions, to read only, disabling me from writing deleting data.

It's been doing this the past few weeks, and it's very annoying.

~ Mel C.

---

### Post by Slim Odds on 2011-10-24
> **Spice Girls said:**
> Lately, when I put in my memory card, USB drives, Ubuntu keeps changing permissions, to read only, disabling me from writing deleting data.

It's been doing this the past few weeks, and it's very annoying.

~ Mel C.

An example of what the permissions were before and after would be very helpful.

---

### Post by oldtimer7777 on 2011-10-24
> **Slim Odds said:**
> An example of what the permissions were before and after would be very helpful.

The 11.10 developers took out an important package that is normally included in Ubuntu:

sudo apt-get install ntfs-3g

---

### Post by Slim Odds on 2011-10-24
> **oldtimer7777 said:**
> The 11.10 developers took out an important package that is normally included in Ubuntu:

sudo apt-get install ntfs-3g

Which is why details (or examples) are critical to determining what the problem is.

---

### Post by Thelinuxgeek on 2011-10-24
open a terminal and type: 

gksu nautilus

Now you won't have to worry about permissions.

---

### Post by Slim Odds on 2011-10-24
> **Thelinuxgeek said:**
> open a terminal and type: 

gksu nautilus

Now you won't have to worry about permissions.

Dangerous and NOT true.

If it's an NTFS you'll still need ntfs-3g installed.

---

### Post by oldtimer7777 on 2011-10-25
ntfs-3g should be installed by default in 11.10.. They should change that back.

> **Slim Odds said:**
> Dangerous and NOT true.

If it's an NTFS you'll still need ntfs-3g installed.

---

### Post by airplanesimen on 2011-10-25
and that mean we have to install it manually? got the same problem...

---

### Post by Slim Odds on 2011-10-25
> **airplanesimen said:**
> and that mean we have to install it manually? got the same problem...

That's what it means....

It's not too hard:```
sudo apt-get install ntfs-3g
```from a terminal window will do it.

---

### Post by airplanesimen on 2011-10-25
> **Slim Odds said:**
> That's what it means....

It's not too hard:```
sudo apt-get install ntfs-3g
```from a terminal window will do it.

and thats it? fixed? Thanks(did know how to install it anyway)...

---

### Post by oldtimer7777 on 2011-10-26
> **airplanesimen said:**
> and thats it? fixed? Thanks(did know how to install it anyway)...

Backrubs are always welcome..  Make sure you close this thread when you are done please.

---

### Post by varunendra on 2011-10-27
> **Slim Odds said:**
> That's what it means....

It's not too hard:```
sudo apt-get install ntfs-3g
```from a terminal window will do it.Are you sure it is not installed by default? Because I just checked it in the Live CD and it is installed there. So I am assuming it should also be included in a native installation. If anything, I would expect a better replacement in default packages, not an elimination of such a useful stuff. That would be a bad idea IMHO.

> **oldtimer7777 said:**
> Backrubs are always welcome..  Make sure you close this thread when you are done please.
That is something only *Spice Girls* (the OP) can do, or the mods :). I'd like to hear more from him/her as this seems an interesting problem.

---

### Post by coffeecat on 2011-10-27
> **oldtimer7777 said:**
> The 11.10 developers took out an important package that is normally included in Ubuntu:

sudo apt-get install ntfs-3g

> **oldtimer7777 said:**
> ntfs-3g should be installed by default in 11.10.. They should change that back.

> **varunendra said:**
> Are you sure it is not installed by default? Because I just checked it in the Live CD and it is installed there. So I am assuming it should also be included in a native installation.

Point of information: ntfs-3g **is** installed by default in Oneiric; the developers did not remove it. The difference in Oneiric is that ntfs-3g now comes with the functionality previously provided by the package ntfsprogs, and ntfsprogs now conflicts with ntfs-3g. I believe some of the problems that people are seeing could be that they are installing ntfsprogs, thinking that they need it, and not noticing that the package manager is prompting for the removal of ntfs-3g.

Some people are suggesting that ntfs-3g has been removed during updates or upgrades from 11.04. All I can say is that I have not observed this in five Oneiric systems, three of which were (successful) upgrades from 11.04.

---

### Post by varunendra on 2011-10-27
Thanks for the valuable information coffeecat. Especially the _conflict related info_ is indeed very important and beneficial for all of us.

---

