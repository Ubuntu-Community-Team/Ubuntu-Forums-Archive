---
title: "Removing xubuntu-restricted-extras from ubuntu server"
date: 2010-08-10
forum: General Help
---

### Post by bjaanes on 2010-08-10
Hi, :D
 
I managed to install xubuntu-restriced-extras on my Ubuntu 10.04 server (which btw is headless and no X installed at all) :P
 
Anyways, i tried to remove it with apt-get remove, but in only deleted a couple of Kb. 
tried with --purge, autoremove, autoclean, clean and everything else i could think of, but my poor server is still bloated with stuff like adobe-plugins and stuff i dont need.
 
How can i propely remove the entire package? I could also remove the package piece by piece (since its just a dummy package, no?), but I tried to search the internet for such information, but to no avail. Where to look, what to do?
 
All help to keep my poor server slim and slick is well appreciated! :KS
 
(btw, this happended because i was installing the package on my xubuntu laptop, but forgot i was SSH'ing to my server :rolleyes:

---

### Post by Brandon Williams on 2010-08-10
It sounds like the recommends for xubuntu-restricted-extras were not marked as automatically installed, which means that they will not be automatically removed when they are no longer needed. You may have to manually purge each individual recommended package.

Alternatively, you could try using deborphan to get a listing of all packages on your system that have no other packages depending on them and then select all the individual packages for removal that you don't need. Be careful with this approach and ensure that you don't remove any packages that you are uncertain about.

---

