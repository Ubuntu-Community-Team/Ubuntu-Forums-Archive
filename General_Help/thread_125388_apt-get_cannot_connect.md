---
title: "apt-get cannot connect"
date: 2006-02-03
forum: General Help
---

### Post by whiterussian on 2006-02-03
Hello world,

This has happened on all of my ubuntu-based machines (everything i run that isnt SuSE), apt-get gets connection refused when trying to contact the update servers. I dont know if its just my area or what, but the servers for me (all the way up in canada... oooh) should be:

ca.archive.ubuntu.com 

With various directories and such, but i get this:

Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) breezy/main gcc-3.4 3.4.4-6ubuntu8
  Could not connect to ca.archive.ubuntu.com:80 (206.75.218.52). - connect (111 Connection refused) [IP: 206.75.218.52 80]

I've resorted to compiling from source, can anyone let me know if these servers have inexplicably moved or what?

Lacking that, gimme the Amerikanski ones.

---

### Post by Adrian on 2006-02-03
Try these repositories:
[http://www.psychocats.net/linux/sources.php](http://www.psychocats.net/linux/sources.php)

---

### Post by whiterussian on 2006-02-03
Merci, those ones seem to work ok.

I dunno what happened to the canadian ones, i cant even scan em'

---

### Post by claud10 on 2006-02-07
4 days after I'm having the same problem. I'm in Québec.
Anyone knows what's going on with the canadian server?

Bye

---

### Post by goatflyer on 2006-02-07
I also commented out my ca. repositories in sources.lst a while ago.  I uncomment them and check every few days but they've been down for awhile.  So its not just me.

---

### Post by jfrese on 2006-02-08
I was having problems with the US-specific servers, and I noticed another post from someone having difficulties with the au servers.  The common advice is to update to the non-country-specific URLs, which usually fixes the problem.  So, no conspiracy against Canadians. (this time!)  :-)

Was there an announcement about the servers that we all missed?

---

