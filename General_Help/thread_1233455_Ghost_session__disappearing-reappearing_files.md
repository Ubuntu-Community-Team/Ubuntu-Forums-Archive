---
title: "Ghost session / disappearing-reappearing files"
date: 2009-08-06
forum: General Help
---

### Post by dehuszar on 2009-08-06
I just had the strangest thing happen.  I booted up my machine and the work I did yesterday was all gone.  Files I downloaded, Wordpress themes I built, a resources library I created in my /var/www/ folder, notes I took for a project in Tomboy.... all gone.  As if yesterday never happened.

Freaked out and in a panic, I shut down, booted back up.  Everything was fine.

I'm now very curious how sessions work.  Are session records written incrementally?  Could data from a certain stretch of time not be properly represented during a particular session?

Very strange.

---

### Post by dehuszar on 2009-08-06
It also appears as though items I was working on in that Ghost Session are now gone.

I should add that there are no users on this machine but me, and I WAS logged in as my user, navigating custom folder structures that only exist in my user's home folder.

Spooky.

---

### Post by dehuszar on 2009-08-06
...and emails that I had downloaded in the Ghost Session had to be re-downloaded from Google.

If possible, I would like to figure out how to reach into this other dimension and grab a few things.  I feel like my data is now at risk of becoming the little girl stuck in the TV.

---

### Post by dehuszar on 2009-08-07
I just rebooted my computer (as opposed to powering it off) and ended up back in the ghost session.  Files I've deleted are back, the same folders and files which were missing from the previous ghost session are gone again.

Perhaps there's a stale lock-file that gets loaded up if I do a soft reboot?  Just stabbing in the dark.  Any ideas are appreciated. 

I'm going to try full shut-down and boot & see if that works.  It did last time.

---

### Post by Universal344 on 2009-08-07
That is very strange...  First, I'd back up the data you want in case the situation gets worse.  Second of all, I think Ubuntu has the ability to save a session to an extent.  However, I didn't think this persisted after a full reboot, but I could be wrong.  Try checking out your session settings to see if it is saving your session and if you may somehow have more than one session.

---

