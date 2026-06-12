---
title: "HELP   Firefox"
date: 2010-07-14
forum: General Help
---

### Post by Quarkrad on 2010-07-14
Clean install of 9.10.  Firefox will not start - Firefox is already running, but is not responding.  to open a new window, you must first close the exiting Firefox process, or restart your system.  I have deleted firefox via Synaptic and reinstalled - still same problem.  Most of the web sites point me towards the .parent and .lock files in the .mozilla folder.  I have deleted these files and still Firefox will not launch (although it will if I type firefox in terminal as root).  There must be another solution other than the lock files - also, a firefox process is definitely not running on my machine.  any help appreciated.

---

### Post by Quarkrad on 2010-07-14
Something I forgot to add - which is key.  On clean install firefox works fine - however, I am trying to copy all the bookmarks etc from a previous install of firefox.  I followed the instructions from Mozilla - I saved the contents of my original .Mozilla folder.  I then copy the firefox folder from the original .mozilla folder to the new install.  When I over write the firefox folder I get the firefox is already running message.

---

### Post by 80aless on 2010-07-14
I also had the same problem: I messed up the ~/.Mozilla folder and I could not fire up Firefox (The error was: "There is another existing process.. kill it.. etc"). 
The solution: simply do not do touch the .Mozilla folder.
You can export and then import the bookmarks with: Bookmarks > Organize Bookmarks > Import and Backups

---

### Post by Quarkrad on 2010-07-15
My solution was to make sure that the owner and group membership of all the imported files and folders were set to the correct owner.  When I copied them across some were changed to root ownership.  Changing them back to the actual machine owner solved the problem.

---

