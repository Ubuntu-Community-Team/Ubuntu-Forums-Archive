---
title: "Biggest mistake I ever made"
date: 2006-02-02
forum: General Help
---

### Post by louis_nichols on 2006-02-02
Well... I'll get to that later.

What I want to ask is where the dpkg system keeps a log somewhere. I mean, separate from synaptic's history. I REEEEALLYY NEED something like that!!

The mistake was that I installed this package, upgrade-system out of curiosity. It came with little documentation, but I figured that, doing something so important, it will need some arguments, some options. Well, it didn't. As soon as I ran it, it started uninstalling a ton of packages from my system. Not all bad, but some programes have stopped working. So... I need to see what it uninstalled, because I don't have the console putput anymore. :(

---

### Post by evs on 2006-02-02
Dpkg stores its log at /var/log/dpkg.log

---

### Post by Lord Illidan on 2006-02-02
Here you are:

In /var/log/ there should be textfiles named dpkg.log (some with numbers after them 1,2,etc), which reveals what you have installed, or uninstalled. Try it.

EDIT : I am too slow.. I need to start typing faster..and jump on evs, too..like I am jumping on the poor peon on the left :)

---

### Post by stuporglue on 2006-02-02
Run apt-get install ubuntu-desktop to get the default packages back again. You may have other non-default packages to install after that, but ubuntu-desktop will grab a big chunch of them for you, I think.

---

### Post by louis_nichols on 2006-02-02
Thank you guys, for the fast answers! They did help. dpkg.log was indeed there (and what a lifesaver it is!! :D) as for the numbered ones... I don't see them, lord. it would be nice, though, to have something like per-session logs. And mayvbe some undo options. Wouldn't THAT be cool? 

Thanks for the tip, stuporglue! I didn't get to use it, because, by the tme I read your post, I had already gone through the log and manually added packages to an apt-install list.

Oh, boy, that was close! The only stupider thing I ever made was to forcefully uninstall glib from one Fedora installation. Needless to say, that was hopeless. :))

---

