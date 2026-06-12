---
title: "Shared todo lists"
date: 2011-06-29
forum: General Help
---

### Post by kelemvor_uk on 2011-06-29
Hi All

Does anyone know of any software that allows shared to do lists? I'm trying to set up a shared todo list for my colleagues and myself that we can access/update over a network.

I've seen that there is software like citadel available but I'm looking for a lighter piece of software rather than having all of the functionality that citadel appears to offer.

Thanks
kel

---

### Post by Habitual on 2011-06-29
tasque

---

### Post by jerrrys on 2011-06-30
what about a simple [bulletin board]("http://en.wikipedia.org/wiki/Bulletin_board_system")

---

### Post by dFlyer on 2011-06-30
Is everyone using linux or is this for a linux/windows/mac setup?

---

### Post by tgalati4 on 2011-06-30
[http://getontracks.org](http://getontracks.org)  which can be installed easily as a bitnami binary blob (statically linked, so it's independent of distro version) from [http://bitnami.org](http://bitnami.org).  If you want to play with it, sign up for a free account at [http://my.gtdify.com](http://my.gtdify.com).

For something simple, you can run zim (sudo apt-get install zim) from a server and have multiple instances open of the same task-list file and the edits automagically propagate to all instances.  

Install zim on all of your linux desktops then point the file to the same task-list file on a shared network folder.  Alternatively, (if you only have one linux machine in the shop), install zim and run remote instances:

ssh -2 -Y user@machine-that-has-zim zim

If your tasker lists look like computer help-desk tickets, then there's a bunch of trackers out there.

apt-cache search ticket

If you want a hosted, web-based system, there's Basecamp at:  [http://37signals.com/](http://37signals.com/)

---

### Post by kelemvor_uk on 2011-06-30
Hi dFlyer

We're looking for something we can run on ubuntu or redhat - preferably ubuntu tho

Some pretty good ideas above - never even considered bulletin boards...will have to take a look :)

Thanks
Kel

---

### Post by kelemvor_uk on 2011-07-07
Hi [tgalati4]("http://ubuntuforums.org/member.php?u=241895")

I've installed Zim and it looks pretty cool, the only thing now is that I'm not sure how to set it up as a shared system. If we're all running ubuntu then I guess one of these has to be the server or share, do you have any ideas on how I can share the files (without using the web feature)??

Zim seems to only want to open local copies

Thanks
Kel

---

### Post by Potters Son on 2011-07-07
If you don't need anything suited for intensive use (like keeping track of a single project), you could make a Google Docs file. You get simultaneous editing plus access from anywhere.

---

### Post by kelemvor_uk on 2011-07-11
Hi

That's a good suggestion but we don't really want to be sending our data out across cyberspace - not that any of it will be very interesting lol. 

We're actually going to try some sort of Tomboy note work around I think - though I think Zim has such a nice look and feel that it'd be a shame not to be able to network it.

Oh well, maybe I should learn how to be a developer and just make something myself - may take a while tho :) (10 years or so lol)

Thanks for all the suggestions guys it's appreciated
Kel

---

