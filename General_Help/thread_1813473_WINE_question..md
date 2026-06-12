---
title: "WINE question."
date: 2011-07-27
forum: General Help
---

### Post by helenacoder on 2011-07-27
Hello,

I'm new to linux. and i went through a couple threads before i decided to start this one.  Here's my problem... everytime i try to do

$ sudo app-get remove wine

i get this error:

E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem.

can someone help me with this?

also, note that I have already used different variations of remove/uninstall/delete commands following instructions from several threads here on how to completely remove wine.

Reasons for removing wine:

I installed an older version. 1.2.2 -- ubuntu software manager has a new/different version as far as i know. 
Thank you to anyone who is wiling to help.

---

### Post by Mark Phelps on 2011-07-27
Yes ... open a terminal and run 'sudo dpkg --configure -a' 

Your package updating is hosed and you need to do this to clean it up first.

---

### Post by helenacoder on 2011-07-27
THANK YOU. figured that out myself sir! oh my goodness this ubuntu thing has so many random issues, but for some reason I like it.  2 days ago I decided to load ubuntu and do an 'install and replace current os'. Thanks for the help.

---

