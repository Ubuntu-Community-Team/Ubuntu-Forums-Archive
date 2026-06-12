---
title: "ubuntu 10.04 stopped booting!"
date: 2010-06-18
forum: General Help
---

### Post by poldie on 2010-06-18
This morning it was fine - i shut it down and went to work.  Now it won't boot up.  It gets to the purple screen with the Ubuntu logo and 5 orange dots, then it goes black almost immediately.  All disk activity stops.  I'm using the same pc now with a live disk, so the pc would seem to be running ok.  I've tried the internal monitor adaptor instead of my ati card - no difference.  I've tried escape or shift during boot but I don't get any text explaining how far I've got.  I've tried booting up 10 times in case it's a rare situation but I get the problem at the exact same time each time.

I'm running 10.04, on a quad core 4 gig system.  I've had no stability problems before. It's a fair new pc (year or two old) I built myself. I update patches all the time.  I might have done so on the last session so it could be that - not sure.  I can see both hard drives on my pc, and I've checked a bunch of files so doesn't seem to be hardware problem or data corruption there.

What do I do now?    Don't have the disk space to copy stuff off my boot drive onto another drive.

---

### Post by Sin@Sin-Sacrifice on 2010-06-18
You might want to add a bit more info about what you were doing before the last shut down before it wouldn't boot. Did you update? Try something new?

---

### Post by poldie on 2010-06-18
> **Sin@Sin-Sacrifice said:**
> You might want to add a bit more info about what you were doing before the last shut down before it wouldn't boot. Did you update? Try something new?

Well, I specifically mentioned updates!   I'm not sure - I update all the time (every few days) - couldn't tell you if any turned up on the last session.  The PC would have been on all night, and I would have turned it off around 8am.  I've done nothing unusual recently.  Certainly no new graphics drivers.  I think I installed a new version of Bibble (photo editor) yesterday.  

Point is, it's failing very early on in the boot process.  I see the purple screen for less than a second and then it dies.  Are there logs which would give a clue?  I'm no a linux pro.  I've looked in var/logs whilst in this live disk session but don't see anything obvious. 

This is a 64 bit system.


Update:  I held shift down during boot, and chose the last kernel.  I got an error during booting about fgrlx not establishing drm connection, and atiddxdriscreeninit failing, but i am now booted up and logged on.  

No idea where to go from here though.  I'm sure I didn't just update a kernel because those always seem to involve a reboot and i've not rebooted after an update for a while.

Tried recovery, but it boots into a command line, no ui, which is useless for me.  It does get there though, and doesn't die on the way.

Booted back into the UI using the previous kernel and still get that fgrlx error, and no 3d.

What do I do now?

UPdate again:  I installed the ati drivers and rebooted (into the 2nd oldest kernel) and it's all working. So the problem now is - how do I get my system working on the latest kernel, instead of the penultimate release?   What's suddenly broken it?  I've not updated graphics drivers for a while.  The latest drivers (they seem to be released every month or so) didn't work so I'm not on the latest ones of those, and to be honest I'm happy sticking with these.  There never seems to be any noticeable difference between graphics drivers anyway, so it's just a monthly waste of 15 mins or so.

---

