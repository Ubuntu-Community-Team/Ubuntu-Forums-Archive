---
title: "how do i install network-manager WITHOUT internet acces"
date: 2009-11-30
forum: General Help
---

### Post by expxe on 2009-11-30
my internet access went poof, now im trying to re-install network manager but it seems to REQUIRE internet access....:-|

is there another way? i still have the install cd. step by step instructions on what is next? im a newb

---

### Post by mac9416 on 2009-11-30
You can get the .deb package at package.ubuntu.com from a Net-connected computer and transfer it over on a flash drive.

---

### Post by expxe on 2009-11-30
there are a lot of dependencies, is there an easier way? can't i get everything off the install cd?

---

### Post by mac9416 on 2009-11-30
Since you need the dependencies, I would recommend using [Keryx]("http://keryxproject.org"). It works like Synaptic, but doesn't have to be run on the system the desired packages are to be installed on. Be sure to read the [tutorial]("http://crashsystems.net/2009/01/keryx-tutorial/") before diving in.

Good luck. :)

---

### Post by expxe on 2009-11-30
> **mac9416 said:**
> Since you need the dependencies, I would recommend using [Keryx]("http://keryxproject.org"). It works like Synaptic, but doesn't have to be run on the system the desired packages are to be installed on. Be sure to read the [tutorial]("http://crashsystems.net/2009/01/keryx-tutorial/") before diving in.

Good luck. :)

ill give this a try, but is there another way? i find it hard to believe i can't grab all the files i need off the install cd

---

### Post by mac9416 on 2009-12-01
I believe you could get the packages from the CD if it was the alternate install CD, but I may be wrong about that. I don't think it's possible with the live CD.

---

### Post by philinux on 2009-12-01
> **expxe said:**
> ill give this a try, but is there another way? i find it hard to believe i can't grab all the files i need off the install cd

You can. You need to use the command unsquashfs. Look up the man pages.

---

