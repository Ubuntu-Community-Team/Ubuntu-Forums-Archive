---
title: "Cannot install Evolution"
date: 2010-06-17
forum: General Help
---

### Post by TheNessus on 2010-06-17
Lucid. I have removed evolution some time ago because I didn't like it. But I missed the level of integration it had with GNOME, so I wanted to install it back.

However:


jeff@jeff-laptop:~$ sudo apt-get install evolution
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  evolution: Depends: evolution-data-server (>= 2.28.0) but it is not going to be installed
             Depends: evolution-data-server (< 2.29.0) but it is not going to be installed
E: Broken packages
jeff@jeff-laptop:~$ sudo apt-get install evolution-data-server
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  evolution-data-server: Depends: evolution-data-server-common (= 2.28.3.1-0ubuntu3) but 2.28.3.1-1ubuntu2~ppa1 is to be installed
E: Broken packages
jeff@jeff-laptop:~$ sudo apt-get install evolution-data-server-common
Reading package lists... Done
Building dependency tree       
Reading state information... Done
evolution-data-server-common is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
jeff@jeff-laptop:~$ 


Which one of you bastards will be my saviour? :)

---

### Post by wojox on 2010-06-17
Try this:

```
sudo apt-get install evolution evolution-common evolution-couchdb evolution-exchange evolution-indicator evolution-plugins evolution-webcal
```

---

### Post by TheNessus on 2010-06-17
Thank you. I did remove couchDB when I removed evo. For good reason, it's a hog, and part of another hog - Gwibber.

---

### Post by dcstar on 2010-06-17
> **TheNessus said:**
> Thank you. I did remove couchDB when I removed evo. For good reason, it's a hog, and part of another hog - Gwibber.

Funny, I have it installed on my system and it "hogs" nothing because nothing is using it.

I can live with the ~4MB of disk space it takes up.

---

### Post by wojox on 2010-06-17
> **TheNessus said:**
> Thank you. I did remove couchDB when I removed evo. For good reason, it's a hog, and part of another hog - Gwibber.

So everything worked out and you got it installed?

---

### Post by TheNessus on 2010-06-17
> **wojox said:**
> So everything worked out and you got it installed?
No, I removed ubuntu and installed #! :)

---

