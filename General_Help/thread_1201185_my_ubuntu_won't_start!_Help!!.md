---
title: "my ubuntu won't start! Help!!"
date: 2009-06-30
forum: General Help
---

### Post by abrax on 2009-06-30
Hello


Okay, here is my problem:

I was trying to do a backup with Remastersys, but i forgot to exclude one folder that has over 100 gigs of information. When Remastersys was trying to make the iso image, it ran out of space in the HDD so the process couldn't finish. The bad thing begins when it all started to ask me for my root pwd, so i went to several pages to look for an answer. I found in one site that if i changed \'s ownership and permissions to my own user, it would stop asking me for the pwd. Now, the REALLy bad thing started when i rebooted and X and the GDM didn't start. I think i screwed things up when i changed the ownerships and permissions, and now i'm desperate because i cant do anything when i'm logged on to my user account. I cannot do anything even logged in the root account and the ownerships of ALL files and folders assigned to root again. HELP PLEASE!!



thanks


EDIT: or is there any way i can fix or reconfigure or replace the system files without reinstalling (because i have a lot of programs and configurations that i don't want to lose and documents  i'm to lazy to backup)
thankyou

---

### Post by blueridgedog on 2009-06-30
You could boot off of a live CD and mount your drive, deleting the remastersys files and archiving any files you wish to retain.  After that a reinstall would probably be the simplest step versus untangling the issue.

---

### Post by abrax on 2009-06-30
> **blueridgedog said:**
> You could boot off of a live CD and mount your drive, deleting the remastersys files and archiving any files you wish to retain.  After that a reinstall would probably be the simplest step versus untangling the issue.

thanks, that was my last resort, but it seems that's the only resort... is there any way i could backup my configuration files and/or the programs i've downloaded so that when i reinstall, the appearance was the same as before?


one more thing that i forgot to say, i installed ubuntu using the wubi installer, so when i tried to mount my partition it only mounted the windows one...

thanks;)

---

### Post by blueridgedog on 2009-07-01
Ah...I was not aware that this was wubi.  I am afraid I have never seen wubi, let alone used it and would be hard pressed to give advice on it.  IF you could access the partition, you could copy over your /home/USER directory and other files.  Perhaps a wubi knowledgeable person will chime in.

---

### Post by abrax on 2009-07-01
> **blueridgedog said:**
> Ah...I was not aware that this was wubi.  I am afraid I have never seen wubi, let alone used it and would be hard pressed to give advice on it.  IF you could access the partition, you could copy over your /home/USER directory and other files.  Perhaps a wubi knowledgeable person will chime in.

thanks anyway and don't worry, i copied all my user config files (the ones in my home directory) and did a fresh install (again with wubi).

Just one more thing happens that im not really sure if it is bad or not, and i dont understand what to do... 

When put my username and password a little 'window' pops up telling me that 'ubuntu will ignore $HOME/.dmrc and that prevents for language to save and the owner of the $HOME folder must be the user' i dont understand why is that, because im the owner of my home folder and also im the owner of that .dmrc file...

thanks

---

