---
title: "root Users Settings"
date: 2011-03-12
forum: General Help
---

### Post by 2901119 on 2011-03-12
To start off I already know the dangers of running as root, please don't waste my time or yours posting about the possible consequences, I'm already well aware.

my problem is, after enabling the root account i noticed a couple issues one of them being when i try to open up users settings it just hangs, this leads me to wonder what other issues im going to run into. 

any help with this matter would be very greatly appreciated.

---

### Post by markeee on 2011-03-12
> **2901119 said:**
> To start off I already know the dangers of running as root, please don't waste my time or yours posting about the possible consequences, I'm already well aware.

my problem is, after enabling the root account i noticed a couple issues one of them being when i try to open up users settings it just hangs, this leads me to wonder what other issues im going to run into. 

any help with this matter would be very greatly appreciated.

not going to waste time re running as root

but when you say user settings -  you mean user manager?

I can't see why running as root would cause it to hang though-works when you login as a non root i assume?

---

### Post by 2901119 on 2011-03-12
by users settings I mean when you go to system>Administration>Users and Groups and it brings up a window titled "Users Settings" but yes when I log into my regular account I can access this no problem. Sound was also disabled by default but I fixed this by adding a start up app for it and pointing it at /usr/bin/pulseaudio

---

### Post by rdh61 on 2011-06-21
Yes, Users Settings hangs when logged in as root. I have found the same issue.

---

