---
title: "Computer tech needs help"
date: 2011-01-03
forum: General Help
---

### Post by frotzed on 2011-01-03
I've done many _many_ Google searches for answers to these questions before coming to the experts (you).  I also wasn't sure of the forum in which to place this thread so mods should feel free to move it as they please.

[SIZE="4"]The Brief Background
[/SIZE]
I've just recently (read: three months ago) started down the path of a professional computer tech for a small local business.  I've been using Ubuntu personally, however, since 6.04.

So I'm 50% bench tech, 50% field tech.  All our customers use Windows and all the other techs at this company use Windows as well.  So I'm learning tools, techniques, etc but they're all Windows based.  For the most part I'm able to translate what I see other techs doing to Ubuntu, it's not that hard.

[SIZE="4"]The Brief Request
[/SIZE]
I'd love to be able to accomplish the same kind of support with Ubuntu and for the most part it's not a problem since most of what I do is using a customer's computer to fix itself... if that makes sense.  Occasionally, however, I'll have to use my laptop (if I'm in the field) or my desktop (if I'm at the shop) to fix a customer's Windows PC.  Here are a few things I cannot figure out how to do on Ubuntu.

1. To check the integrity of a HDD we'll use [SeaTools for Windows]("http://www.seagate.com/www/en-us/support/downloads/seatools").  It's a great tool for pulling a drive from a computer and testing it on a separate PC.  I understand how to use the SMART tool on Ubuntu to test it's own storage, but is there anything I can use aside from the Seatools for DOS when I'm on my Ubuntu machine?

2. I really love [Snadboy Revelation]("http://www.softpedia.com/get/Security/Password-Managers-Generators/SnadBoy-s-Revelation.shtml"), especially when I'm migrating a customer's data from an old PC to a new one.  Has anyone come across something like this for Linux?  It doesn't function correctly in Wine :(

Aside from those two things I feel very good about using Ubuntu to trouble-shoot networks and customer computer issues.  I'm curious if there are any other computer techs out there who rely on Ubuntu for their field and shop work?  If so, what advice would you give to someone just starting out in this field?

---

### Post by deserthowler on 2011-01-03
> **frotzed said:**
> 

1. To check the integrity of a HDD we'll use [SeaTools for Windows]("http://www.seagate.com/www/en-us/support/downloads/seatools").  It's a great tool for pulling a drive from a computer and testing it on a separate PC.  I understand how to use the SMART tool on Ubuntu to test it's own storage, but is there anything I can use aside from the Seatools for DOS when I'm on my Ubuntu machine?

2. I really love [Snadboy Revelation]("http://www.softpedia.com/get/Security/Password-Managers-Generators/SnadBoy-s-Revelation.shtml"), especially when I'm migrating a customer's data from an old PC to a new one.  Has anyone come across something like this for Linux?  It doesn't function correctly in Wine :(



1.  Look at the man page for badblocks.  It can be run from a live CD or from the gparted CD.  Make sure you understand the switches for destructive and nondistructive testing of a disk.

2.  There are a couple of CDs that can be run live that will find and remove passwords as well as move data.  You can try the various ones to see which works best.  There is also some information on recovering or changing passwords using Ubuntu live CD.

Earl

---

