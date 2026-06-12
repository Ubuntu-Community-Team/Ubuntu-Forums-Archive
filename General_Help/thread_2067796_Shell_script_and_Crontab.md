---
title: "Shell script and Crontab"
date: 2012-10-07
forum: General Help
---

### Post by Ubuk2008 on 2012-10-07
Hey all!

I am trying to have a shell script open up a document at specific times each week. This is what I want to achieve. I was wondering if anyone out there knew how one would go about writing a simple shell script to launch the file located in, let's say, Desktop on a regular basis using Crontab?

I haven't been successful in Googling a solution to this and so I hope someone here can help me out. 

Thanks for any tips!

---

### Post by gnuser12 on 2012-10-07
Hello,
install Scheduled Tasks which uses cron 
It has a graphical user interface to manage several recurrent tasks
```
sudo apt-get install gnome-schedule
```
[http://gnome-schedule.sourceforge.net/](http://gnome-schedule.sourceforge.net/)

---

### Post by cipherboy_loc on 2012-10-07
Why not use the at command? Cron is more used to make sure that once every period of time the command gets run (and not necessarily that precise), whereas at runs a command at a specific time, ie, 12:00 January 1, 2013.

For more information, run
```

man at

```

Thanks,
Cipherboy

---

### Post by Ubuk2008 on 2012-10-08
Thank you both for your replies! I found them both resourceful. The 'at' command is particularly handy.

---

