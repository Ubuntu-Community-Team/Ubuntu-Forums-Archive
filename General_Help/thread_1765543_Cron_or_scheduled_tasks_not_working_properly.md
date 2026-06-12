---
title: "Cron or scheduled tasks not working properly"
date: 2011-05-23
forum: General Help
---

### Post by amikebous on 2011-05-23
Hi evebody

I am having a fatal problem with scheduled tasks:

I am running a series of operations on executable matlab scripts which are connecting python and fortran scripts. I schedule the executables in cron. The problem:

- My original matlab scripts work perfectly. 
- My executables work perfectly if I run them from the terminal. - Using the gui scheduled tasks and running the scripts once from a button, everything also works fine. 
- But when I leave the scheduled tasks run on their own, I get an error! The error can be that the script hangs in general (I have some text logs exported every step to track the progress), or I get an error which never appears when I run the script
with any of the other mentioned ways.

- I tried both cron command prompt or the GUI scheduled tasks
- I am running on Ubuntu 64 bit

I have tried several things and I am desperate for solutions, so any ideas are welcome...

Michalis

---

### Post by hwttdz on 2011-05-25
Cron tasks don't have the same environment variables as things run from the terminal.  So I might check that.  You could even do 
env|perl -pe 's/^/export /g' > terminal_environment
and then do a "source terminal_environment" before the cron command you want,
i.e. "source ~/terminal_environment; cron_command" otherwise you're going to have to be more specific about the error.

---

### Post by bleutyler on 2011-05-25
I had problems running a simple /bin/cp command from my crontab.  I understand your frustration!

The workaround that I discovered was to put the /bin/cp command into a bash script.  That bash script is then run from the crontab and it works fine.  

Perhaps a bash wrapper script may help?

---

### Post by hwttdz on 2011-05-25
Cron is really an amazing tool once you get used to it.  
My crontab:
1) calculates the time of sunrise and rewrites itself with a daily alarm based on the time of sunrise
2) does daily archiving
3) empties any old files from the trash
4) makes a homepage with all sorts of information (news headlines, weather report, photos of the day) and displays it and starts playing music for my alarm
5) keeps my computer up to date

I encourage you to play with it and figure out what it can do for you.

---

