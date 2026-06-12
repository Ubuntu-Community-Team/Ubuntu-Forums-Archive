---
title: "Slow Start-up Programs"
date: 2006-05-07
forum: General Help
---

### Post by BitTorrentBuddha on 2006-05-07
What can I do to speed up my start-up programs during a session? Currently it takes a good 3-4 minutes for all the start-up programs to launch. The first one on the list is firestarter, and it starts right away (I set it to 48 instead of default 50.) How can I speed up this process? Can I put all the programs into one script and just run that, if so how can I get multiple programs to run from one script? I'm assuming that it's something due to the way the start-up programs are managed, considering I can start up several programs while the actual start-ups are still loading.

---

### Post by BitTorrentBuddha on 2006-05-08
bump

---

### Post by BitTorrentBuddha on 2006-05-09
bump = (

---

### Post by kbudurka on 2006-05-09
Why are you rebooting so frequently to have it bother you? Perhaps you can post the reasons, and we can give you some commands to restart specific services rather then rebooting.

---

### Post by BitTorrentBuddha on 2006-05-09
Most oftenly because gmail-notify freezes up and a killall doesn't remove the blank space in the panel where it was, so nothing major that I absolutely must restart for.

---

### Post by timmytron on 2008-03-06
> **BitTorrentBuddha said:**
> Most oftenly because gmail-notify freezes up and a killall doesn't remove the blank space in the panel where it was, so nothing major that I absolutely must restart for.

i have the same problem with gmail-notify. however, try killing the process labeled "python" instead of gmail-notify. it will kill gmail & remove the space.

---

### Post by mcduck on 2008-03-06
> **BitTorrentBuddha said:**
> Most oftenly because gmail-notify freezes up and a killall doesn't remove the blank space in the panel where it was, so nothing major that I absolutely must restart for.

"killall gnome-panel" should do the trick for you (restarting the panel & all panel applets).

Anyway, if you are having problems with gmail-notify try the Mail Notification applet instead, it supports gmail accounts as well as POP/IMAP accounts..

What comes to startup programs, are you sure you really need to start that many apps automatically? Starting many apps at the same time will be slow no matter what. I'd suggest going through the apps and removing every one you don't absolutely need, for example there's no reason to run the Firestarter configuration tool all the time, the firewall will work without it anyway..

---

