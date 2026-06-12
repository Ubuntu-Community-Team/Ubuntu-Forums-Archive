---
title: "Lucid-Update Manager-Not updating date"
date: 2010-06-03
forum: General Help
---

### Post by emarkay on 2010-06-03
Anyone else notice that the date is no longer changing - I just updated a few minutes ago,  and have seen this since it said "3 days ago"...

Confirm so I can file a bug

---

### Post by colorlessprism on 2010-06-03
i can also confirm this, but could not get anyone to confirm on #ubuntu. i have have to manually check/run the update manager.

Make: MSI
Brand: Wind
Model: U123
OS Ver: 10.04UNE
"dmidecode -s" results shown below
system-manufacturer: MICRO-STAR INTERNATIONAL CO., LTD
system-product-name: MS-N033
system-version: Ver.001

EDIT:
my apologies my update manager does not notify me automatically anymore. i thought thats what this post was in regard to

---

### Post by emarkay on 2010-06-04
[QUOTE=colorlessprism;9406371EDIT:
my apologies my update manager does not notify me automatically anymore. i thought thats what this post was in regard to[/QUOTE]


Yes,  the "8 days ago" in the above screencap is the issue ; it says "9 days ago" now... :)

---

### Post by wiebeest on 2010-06-04
> **emarkay said:**
> Yes,  the "8 days ago" in the above screencap is the issue ; it says "9 days ago" now... :)
Same trouble here I can confirm. Just aesthetical bug it seems, because it does seem to perform it's updates flawlessly.

Another weird thing, pressing "check for updates"button afterwards again, it askes me for password and all of a sutton a bunch of new updates appear (???) This seems to work every time I boot Ubuntu 10.4 the other day...what gives??

---

### Post by emarkay on 2010-06-06
What package would this be to report a Launchpad bug, I wonder?

---

### Post by Queue29 on 2010-06-07
The problem is not with Ubuntu directly (and is a very known issue, no need to report), it's that the getdeb servers are and have been down for over a week now. No getdeb = missing updates = most recent complete update for your system is the last time that getdeb was running when you updated. 

[http://www.ubuntugeek.com/getdeb-mirror-site.html](http://www.ubuntugeek.com/getdeb-mirror-site.html)

---

### Post by emarkay on 2010-06-07
> **Queue29 said:**
> The problem is not with Ubuntu directly (and is a very known issue, no need to report), it's that the getdeb servers are and have been down for over a week now. No getdeb = missing updates = most recent complete update for your system is the last time that getdeb was running when you updated. 
[http://www.ubuntugeek.com/getdeb-mirror-site.html](http://www.ubuntugeek.com/getdeb-mirror-site.html)

So confirm - if a repo is "down", regardless of the remaining "up" ones, the date will** NOT** increment, _even though the remaining data is actually updating_?
This does then, sound like a bug...   I'd want to know the "latest, any" not the "latest, all" update info!

---

