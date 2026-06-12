---
title: "removing electricsheep"
date: 2009-12-15
forum: General Help
---

### Post by cometdog on 2009-12-15
Hi all,

I was playing around with screensavers and tried to install electricsheep.

The first version I tried didn't work (repositories or .deb, don't recall), and the website recommended installing a newer version from the makesheep.sh script.  I dutifully downloaded and ran the script to compile and install.  No errors that I recall, and previewing the electric sheep works.  However, my screen just turns blank when the screensaver kicks in.

At this point, I would really like just to remove the electric sheep program, but as I installed it via a script, I really don't have much clue how to go about doing this.  I could run around my computer searching for "electricsheep" and deleting things that I find.  But perhaps there's a better way?  Anyone here have any experience with that?

---

### Post by Matt__ on 2009-12-15
err...tried
```
sudo apt-get remove electricsheep
```

---

### Post by cometdog on 2009-12-15
Yeah, sorry, it was buried in my post that I did not install from a repository or from a .deb file.

The issue is that I installed from makesheep.sh script.  Don't know how to remove in that case.

Just for completeness I tried your suggestion just now and as expected it said
```
Package electricsheep is not installed, so not removed
```

---

### Post by finlost on 2010-01-30
My Ubuntu knowledge is weak, so I might get called out on this.  AFAIK, you have to delete each subdirectory to expunge electricsheep.

---

