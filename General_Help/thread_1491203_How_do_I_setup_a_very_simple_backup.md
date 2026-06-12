---
title: "How do I setup a very simple backup?"
date: 2010-05-23
forum: General Help
---

### Post by esoikie on 2010-05-23
I have a second HD in my computer for doing a backup onto.  All I want is to select a couple of my documents folders and have them copied to it daily.  I would like it to add new files and update newly modified ones.  I don't want it encrypted or archived, just a basic copy.  How can I set this up to automatically run every night?

---

### Post by Zemblan on 2010-05-23
Déjà Dup is a pretty simple but useful backup utility with a straightforward interface. You can find it in the Software Centre.
Another way to do it would be to make a simple shell script to copy the files, and then use cron to schedule that script to run whenever you want.

---

### Post by colorlessprism on 2010-05-23
rsync is an open source utility that provides fast incremental file transfer. rsync is freely available under the__ GPL and is currently being maintained by Wayne Davison.

check it out and see if it will work for you

[http://samba.anu.edu.au/rsync/documentation.html](http://samba.anu.edu.au/rsync/documentation.html)

---

### Post by esoikie on 2010-05-23
of course... RTFM... 
cp -ur source/dir destination/dir

the -u flag will only update new and updated files.  Should have read the man pages.  Now if I can figure out cron...  I'll be back if I can't. :D

---

### Post by esoikie on 2010-05-23
Wow... a small script dropped into /etc/cron.daily/ was a pretty simple solution.  Thanks.

---

