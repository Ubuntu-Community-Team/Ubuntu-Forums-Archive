---
title: "rsync, how to backup daily modified files"
date: 2010-03-04
forum: General Help
---

### Post by Gingalone on 2010-03-04
Hallo everybody,
I am starting to use regularly rsync as a powerful tool to backup my work.
Now it would be very useful for my purposes to backup automatically all those files that have been created or modified today (I mean in a day of work).
I had a look in the rsync man page but I am not expert enough to dig into filter rules etc...
Any advice?
Thanx in advance, ciao,
Gingalone

---

### Post by HermanAB on 2010-03-04
Put the backup script in /etc/cron.daily

---

### Post by richardjh on 2010-03-04
Do you mean you want to use rsync to effectively copy files created or modified today and run the script daily and not backup any other files?

Why not just rsync all files at the end of each day? 
Only those that have been created / modified will get synchronized anyway.

I can provide you a backup script of that is what you are after.

---

### Post by Gingalone on 2010-03-04
Thank you richardjh and HermanAB,
my idea was just to copy the files created and modified in a work session in order to have a quick backup (I already have a home dir rsync backup script but it takes a long copying time because every time it copies the Vbox virtual HD file (3 GB) even if I didn't work with Vbox and that alone takes 15 min time to be copied... 

Alternatively it would be useful to have an option request when executing the rsync script about the backup of the vbox big file, I mean a prompt like:"do you want the Vbox HD file copied? Y/N".
But I am a beginner with command scripts and don't know how to put a prompt for input in a command file... Sorry about that!!!
Thaaaanks again, ciao,
Gingalone

---

### Post by psusi on 2010-03-04
The whole point of rsync is that it copies only data that changed since the last time.  If it doesn't seem to be doing that then you must be using it wrong, but you haven't given any information on how you are using it.

---

### Post by switch10 on 2010-03-04
Yes I have the same problem with rsync and that .VirtualBox directory.  I found that that VBox dir is constantly changing, so rsync has to copy it every time.  I finally settled on the 
```
 --exclude .VirtualBox 
```
option.

Why not setup another cron job to back up that virtualbox dir, on a not so regular basis?  That may work well for you.

---

### Post by Gingalone on 2010-03-08
thanks everybody for help! :p
Ciao,
Gingalone

---

