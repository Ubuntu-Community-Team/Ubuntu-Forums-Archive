---
title: "Cant Download updates and new software wont install"
date: 2006-02-22
forum: General Help
---

### Post by gearz on 2006-02-22
i do not have the internet and i need to insatll updates and new software is there a way arround this

---

### Post by Zeroangel on 2006-02-22
Use your magic-cow powers.

Make a list of stuff that you want for your computer (like to edit audio files, you will want Audacity) Take your tower over to someone who has the internet, hook up their monitor, keyboard and mouse, then download the updates from there. Use and application like Automatix to download the most frequently used programs, then search around in Synaptic for anything else you might want. It will take you at least 3 hours to get everything you want if your friend/family are using high-speed internet.

---

### Post by gearz on 2006-02-22
ok thanks. i will do that. it would make it a lot easyer if o could download them and transfur them via memory stick. if there is a way please reply. i am also installing fedora on my pc. will i have to do the same with that? 

.:: Gearz ::.

---

### Post by lamego on 2006-02-22
You can get the .deb files from 
[http://us.archive.ubuntu.com/ubuntu/pool/](http://us.archive.ubuntu.com/ubuntu/pool/)...
Then you can install them with dpkg -i package.deb .
Anyway it will be a pain because of packages dependencies...
I would get an ubuntu system into the internet, do the installs/upgrades and then copy the /var/cache/apt (I think is the correct place) files over to the new system.
I believe you could do this with a livecd version.. if you can't afford to install ubuntu on the internet "PC".

---

