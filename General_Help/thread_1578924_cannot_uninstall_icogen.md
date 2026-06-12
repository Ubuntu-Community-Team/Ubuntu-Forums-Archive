---
title: "cannot uninstall icogen"
date: 2010-09-21
forum: General Help
---

### Post by gandaran on 2010-09-21
I'm having this problem, tried to remove icongen and the application did not remove completely, theres something wrong with this package, now icongen is stuck in synaptic package manager, its marked for removal and it wont let me unmark it so I cant reinstall it or install or remove any other package.
I have run out of ideas for a fix.
any magic command to clear this up?

---

### Post by gandaran on 2010-09-22
bump

---

### Post by gandaran on 2010-09-23
bump

---

### Post by na5h on 2010-10-16
I had the same problem!
Take a look at this thread:
[http://ubuntuforums.org/showthread.php?t=1566679]("http://ubuntuforums.org/showthread.php?t=1566679")

Here's my own solution (I think that this is an easier way):
Open a terminal and type "sudo nautilus" to use the Nautilus file-browser as superuser (remember to be careful when you use Nautilus as superuser). Open the folder /usr/share (located in "File System"). Create a new folder named "icoGEN" inside /usr/share, then create a new empty file inside your new folder (right click->Create Document->Empty File). Now, open a terminal and type "sudo apt-get autoremove". The problem should be gone (worked for me)!

---

### Post by gandaran on 2010-10-17
> **na5h said:**
> I had the same problem!
Take a look at this thread:
[http://ubuntuforums.org/showthread.php?t=1566679]("http://ubuntuforums.org/showthread.php?t=1566679")

Here's my own solution (I think that this is an easier way):
Open a terminal and type "sudo nautilus" to use the Nautilus file-browser as superuser (remember to be careful when you use Nautilus as superuser). Open the folder /usr/share (located in "File System"). Create a new folder named "icoGEN" inside /usr/share, then create a new empty file inside your new folder (right click->Create Document->Empty File). Now, open a terminal and type "sudo apt-get autoremove". The problem should be gone (worked for me)!
thank you for your answer
well in fact I did have the same idea, I created a /usr/share/icoGen/data folder (no files) then the icogen application did remove completely or not very completely as it still left the  /usr/share/icoGen in the file system removing only the data folder but at least it got rid of it in synaptic.

---

