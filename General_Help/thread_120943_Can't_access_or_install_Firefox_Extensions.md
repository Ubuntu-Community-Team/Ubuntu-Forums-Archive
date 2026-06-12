---
title: "Can't access or install Firefox Extensions"
date: 2006-01-23
forum: General Help
---

### Post by dolphinholmer on 2006-01-23
Rather bizarely when I click on tools and then extensions the expected dialog box no longer appears. I'm also now unable to install any new extensions and am rather baffled. I tried re-installing Firefox with Synaptic but this did not solve the problem. I considered unistalling firefox and then deleting all the firefox related folders in my home directory before re-installing, but thought I'd seek guidance first.

---

### Post by Sp@z on 2006-01-24
I assume you are using version 1.07 since you reinstalled with synaptic..........you can always download and use automatix to update to the newest firefox...make sure if you are using gnome to install the gnome version....and follow the directtions to back up your favorites and such if you have them left...

[http://www.ubuntuforums.org/showthread.php?t=66563&highlight=automatix](http://www.ubuntuforums.org/showthread.php?t=66563&highlight=automatix)

Good luck!

---

### Post by pbb on 2006-01-24
Can you close Firefox (and all extra windows, like the download manager), and then start "mozilla-firefox" from the terminal? That way you will get to see any error messages the application spawns.
Try opening the extension manager now, and see what error messages you get.

---

### Post by dolphinholmer on 2006-01-24
Yes it's version 1.0.7, I'll install 1.5 only if I can't get this to work!
I ran Firefox from the terminal, no error message and exactly the same problem as before with no error messages when extensions failed to open. I then ran firefox as root and received the following:
You should really not run firefox through sudo WITHOUT the -H option.
Anyway, I'll do as if you did use the -H option.
*** loading the extensions datasource
*** loading the extensions datasource

In this instance of Firefox the extensions opened and all was well.

---

