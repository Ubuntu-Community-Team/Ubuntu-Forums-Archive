---
title: "HDD encryption information requested"
date: 2006-04-19
forum: General Help
---

### Post by eternal on 2006-04-19
hey all.

so, i was mentioning ubuntu around work, and i guess i got someones attention with it...  i was asked to "test and proof" a company spec. system based on ubuntu.  yay! right?  well...

here's what needs to be accomplished:
1) Boot off of a CD (or DVD)
2) allow for the entire hard drive to be encrypted.

so, the core of the basic OS needs to be essentially removeable and read only.  all writeable sectors will be on encrypted harddrives, and won't be accessable until mounted.

this is honestly beyond the scope of what i have personally used Ubuntu for, and i am hoping that some kind soul here may have some knowledge on the topic.

all i can really say about the company's current rigs is that they are BSD based, and running GEOM Based Disk Encryption.  i havent been able to find any (seemingly) on-topic stuff by google-ing...

it'd be really nice to beat this hurdle, because they really like the prospect of the wine windows emulator for easy running of legacy apps.  and as far as i'm concerned, the more i can do to keep anyone from having to go to mr. gates, the more i will do.

thanks in advance.
:confused: 
shaun

---

### Post by mips on 2006-04-19
As far as i know Linux does not have support for GEOM or GELI at the moment.

Google for Linux Disk Encryption.

[http://www.infoanarchy.org/wiki/index.php/Hard_Disk_Encryption#For_UNIX-like_systems](http://www.infoanarchy.org/wiki/index.php/Hard_Disk_Encryption#For_UNIX-like_systems)

From a security point of view I would pick BSD before Linux but you could also make linux more secure. Just think it is easier with BSD.

---

### Post by eternal on 2006-04-19
thanks -=o)  checking now.

---

