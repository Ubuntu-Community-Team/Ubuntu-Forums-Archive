---
title: "Suddenly Evolution wants to use Setup Assistant - why?where has my email account gone"
date: 2009-11-27
forum: General Help
---

### Post by getglenn on 2009-11-27
today i started Evolution and was greeted with the 'setup assistant'

emails were working ok last time i used it!

i dont want to touch any thing until i can find out what happened or what i can do to recover or correct the problem

i have looked in /home/user/.evolution and a folder for my email address is still there, but am not sure how to restore it

i am still 'googling' the problem and any help would be appreciated

---

### Post by dcstar on 2009-11-27
> **getglenn said:**
> today i started Evolution and was greeted with the 'setup assistant'

emails were working ok last time i used it!

i dont want to touch any thing until i can find out what happened or what i can do to recover or correct the problem

i have looked in /home/user/.evolution and a folder for my email address is still there, but am not sure how to restore it

i am still 'googling' the problem and any help would be appreciated

Various account setup details are stored in the some of .gconf files in you /home folder.

You may want to do a fsck (using a Live CD) and see if things change.

---

### Post by getglenn on 2009-11-30
actually, i should have mentioned in my post that the problem came after ubuntu froze... i rebooted and up came the message that i needed to do a manual fschk... which i did [using a live cd]

after correcting the errors it found, when i booted into gnome evolution wanted to go through setup

---

### Post by wata on 2009-12-05
I just ran into exactly the same problem.  Yesterday email/evolution was working fine.  I shutdown my computer (gracefully), powered up today and Evolution starts into the Setup Assistant.  I rebooted and forced fsck, but no errors were found - starting Evolution still just brings up the Setup Assistant.  Any help on this is appreciated.

---

### Post by wata on 2009-12-07
> **wata said:**
> I just ran into exactly the same problem.  Yesterday email/evolution was working fine.  I shutdown my computer (gracefully), powered up today and Evolution starts into the Setup Assistant.  I rebooted and forced fsck, but no errors were found - starting Evolution still just brings up the Setup Assistant.  Any help on this is appreciated.

In case anyone else runs into this problem and ends up on this page.  I started filling in the Setup Assistant fields to see what would happen (I backed up my ~/.evolution directory first).  However I then ran into this bug: [https://bugs.launchpad.net/ubuntu/+source/evolution/+bug/427953](https://bugs.launchpad.net/ubuntu/+source/evolution/+bug/427953) :-(

I then used the Synaptic Package Manager and re-installed Evolution and removed evolution-plugins-experimental (just in case that was causing my grief).  After the re-install, Evolution would still start into the Setup Assistant, but at least I could past the "apply" button (bug 427953).  Once I had completed the setup all my emails were back and everything (so far) looks normal =D>.

Note this epic journey was with Ubuntu 9.10 and Evolution 2.28.1

---

### Post by getglenn on 2009-12-14
before i could try the suggestions from wata and dcstar, on rebooting i have many errors, and i am dropped into a login prompt... 

after entering my user name and password i'm told that the user doesnt exist and ubuntu can't access the password database

i assume that correcting the errors fschk found on the disk has removed essential files, so i will backup /home with the live cd and reinstall ubuntu and hope i dont lose too much data

---

### Post by glendavee on 2009-12-23
Having same problem. After a power failure, rebooting and opening evolution takes me to the setup assistant. All my /.evolution files are there, but I'm not sure what to do when setup asks for a backup file. I've never specifically backed up evolution. Any suggestions welcome.

---

### Post by dcstar on 2009-12-23
> **glendavee said:**
> Having same problem. After a power failure, rebooting and opening evolution takes me to the setup assistant. All my /.evolution files are there, but I'm not sure what to do when setup asks for a backup file. I've never specifically backed up evolution. Any suggestions welcome.

The .evolution folder contains all of your old data, just rename it and allow Evolution to create a fresh one - then copy the files you want from the old one to the new one.

If people have a separate /home partition it is less likely to suffer corruption by a crash in the root filesystem (and you can reinstall as many times as you want without affecting your existing user data).

---

### Post by glendavee on 2009-12-23
Solution very simple. I've just reinput all my account details via the setup assistant, and everything is back to normal.

---

### Post by getglenn on 2009-12-28
none of the suggestions worked, so i opted to re-install ubuntu... choosing to **format** the / partition but **not** the /home partition.

after a reboot, all my evolution data was again available... nothing was **lost!**

i'm not so sure recovery would have been so successful if i was using ms windows

many thanks to all who took the time to reply

---

