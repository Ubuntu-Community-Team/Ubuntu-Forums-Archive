---
title: "How am I using 11.04 Natty Narwhal?"
date: 2011-01-28
forum: General Help
---

### Post by Red Kelly on 2011-01-28
I just clicked on System>About Ubuntu and it tells me "You are using Ubuntu 11.04 - the Natty Narwhal - released in April 2011 and supported until October 2012."
How can this be? It is only January and I installed 10.10 about a month ago.
I have been fiddling with things trying to get my network up but I don't remember upgrading.

---

### Post by Primefalcon on 2011-01-28
> **Red Kelly said:**
> I just clicked on System>About Ubuntu and it tells me "You are using Ubuntu 11.04 - the Natty Narwhal - released in April 2011 and supported until October 2012."
How can this be? It is only January and I installed 10.10 about a month ago.
I have been fiddling with things trying to get my network up but I don't remember upgrading.
read my post here: [http://ubuntuforums.org/showthread.php?t=1677554#td_post_10407592](http://ubuntuforums.org/showthread.php?t=1677554#td_post_10407592)

---

### Post by Red Kelly on 2011-01-28
Thanks looks like they are getting ahead of themselves :)

---

### Post by Red Kelly on 2011-01-28
oh and how do i find if i'm using 32bit or 64 that was the reason i looked in the first place?

---

### Post by Primefalcon on 2011-01-28
cat /proc/version

see if it says x64 or not in there

---

### Post by Primefalcon on 2011-01-28
Also you could run ```
apt-cache search --installed linux-image
``` to see if it says x86 or x64 with x64 being 64 bit and x86 being 32 bit

---

### Post by Red Kelly on 2011-01-28
thanks

---

### Post by Primefalcon on 2011-01-28
your welcome :)

---

### Post by pete_m on 2011-01-29
off-topic:

Cheers for the Dropbox link - I'll be looking at it and looking for an API

on-topic:

Sounds like this user - like myself not long ago- needs some information about Debian & Ubuntu release cycles and how kernel and applications
Anyone know where there's a  good explanation of this ?

I've now ended up pinned to Debian Sid having upgraded ( with some pain) from what was orginally a karmic install on my netbook.. There are increasingly few ubuntu-branded packages on the machine. 

Blender being the notable PPA exception.
 But I am about to use the Natty repos and see what's about ([ LibreOffice 3.3  ]("http://ubuntuforums.org/LibreOffice%203.3%20has%20been%20released.%20Here%20is%20the%20announcement:%20%20http://listarchives.documentfoundati.../msg00026.html") )
The machine was pretty broken at some stages and was rescued from stick and latterly another linux instance on a separte partition.
I'm running 2.6.35 kernel and haven't looked at upgrading for some months.


more in this vein at
[http://placid-linux.icefactory.heliohost.org ]("http://placid-linux.icefactory.heliohost.org")



Continuous apt-get upgrades have resulted in great improvements - gnomeshell was dead when first installed but when recenttly re-visted ran well.

---

### Post by t3s7a on 2011-02-01
OMG it's April 2011 already??????
Time just seems to fly on Unix systems

:lolflag: 

Funny BuG

---

