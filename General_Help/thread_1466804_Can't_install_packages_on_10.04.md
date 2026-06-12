---
title: "Can't install packages on 10.04"
date: 2010-04-30
forum: General Help
---

### Post by Zyrtec on 2010-04-30
Whenever I do sudo apt-get or use the Ubuntu Software Center, I can't download anything because a message comes up saying "Action requires installation of untrusted packages: The action would require the installation of packages from not authenticated sources."

I've been trying to download GIMP and Thunderbird, so... I dunno what the problem is.

Thanks!


Edit: I even tried using the update manager to get some updates that have to do with Medibuntu, and it won't let me download from that either. o__O

---

### Post by pqwoerituytrueiwoq on 2010-04-30
that happened to me when i tried to install bleachbit with the gui
i clicked install again and it worked
not sure how that works from the terminal

---

### Post by chessnerd on 2010-04-30
I just had this happen as well. 

Reload the software sources (Synaptic's Reload button) and it will fix it. (Although it might take a couple of tries to reload them...) 

Canonical's servers are working overtime at the moment. You can't expect too much from them right now.

---

### Post by pqwoerituytrueiwoq on 2010-04-30
> **chessnerd said:**
> I just had this happen as well. 

Reload the software sources (Synaptic's Reload button) and it will fix it (although it might take a couple of tries to reload them). 

Canonical's servers are working overtime at the moment. You can't expect too much from them right now.
took me like 20 minutes to just to a sudo apt-get update

---

### Post by chessnerd on 2010-04-30
> **pqwoerituytrueiwoq said:**
> took me like 20 minutes to just to a sudo apt-get update

Same here. Even just loading the software sources is buggy and slow, which is probably what is causing this problem. Downloading packages can be really hit or miss and, when it works, often takes a long time. It took over an hour to get the packages for Eclipse last night...

Stupid new releases! Give it a few days and things should be back to normal.

---

### Post by lunaparadox on 2010-04-30
I'm having issues with synaptic when ever I try to install anything through it my machine just freezes up and have to do a hard reset. installing through terminal no problem. downloading .deb packages and trying to install from hard drive causes freezing as well. so far 10.04 is good for surfing the net and thats about it. even playing music is causing freezing. back in 9.10 for now just discouraged with it all:confused:

---

### Post by enonymous99 on 2010-04-30
I am also getting "Action requires installation of untrusted packages" not able to install anything.

---

### Post by enonymous99 on 2010-04-30
It is working for me now.

---

### Post by Zyrtec on 2010-04-30
Thanks for the help guys. I was lead in the right direction, at least.

I went into synaptic > preferences > repositories

And somehow, the actual Ubuntu 10.04 Repositories by Canonical were unchecked. I checked their boxes, and then reloaded, and now everything seems fine.

---

