---
title: "ubuntu software center failing me"
date: 2011-08-22
forum: General Help
---

### Post by sdowney717 on 2011-08-22
on an older 2.4 ghz, it is eating up the CPU 100%

I noticed I tried to install google chrome from a deb was failure so I had to install using a PPA.
Now I want to install a deb for thevoice chat plug in and it is failing

so what to do??
app appears to lock up with progress bar barely moved.
I am currently using the computer to post and things still work.

---

### Post by sdowney717 on 2011-08-22
it cant be that slow! many minutes have gone by
how else to install a deb file?
how to reinstall the software center?

---

### Post by sdowney717 on 2011-08-22
> scott@scott-MS-7104:~/Downloads$ sudo dpkg -i google-talkplugin_current_i386.deb 
dpkg: error: dpkg status database is locked by another process
scott@scott-MS-7104:~/Downloads$ sudo dpkg -i google-talkplugin_current_i386.deb 
dpkg: error: dpkg status database is locked by another process
scott@scott-MS-7104:~/Downloads$ 


of course locked because software center is locked up

name to kill?, I think it is hosed.

---

### Post by sdowney717 on 2011-08-22
> scott@scott-MS-7104:~/Downloads$ sudo dpkg -i google-talkplugin_current_i386.deb 
Selecting previously deselected package google-talkplugin.
(Reading database ... 191721 files and directories currently installed.)
Unpacking google-talkplugin (from google-talkplugin_current_i386.deb) ...
Setting up google-talkplugin (2.2.2.0-1) ...
scott@scott-MS-7104:~/Downloads$ 


installs fine from command line and gmail video plugin is working

---

### Post by Script Warlock on 2011-08-22
i don't think USC can handle well a deb with a missing dependencies i'd rather use dpkg -i to install things.

---

### Post by realzippy on 2011-08-22
Yep,there seems to be something rotten in software center the last days...

---

