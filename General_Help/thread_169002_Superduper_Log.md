---
title: "Superduper Log"
date: 2006-05-01
forum: General Help
---

### Post by ububaba on 2006-05-01
Do I remember wrongly, having read, that somehwhere in Ubuntu, there is a [COLOR="Red"]master[/COLOR]
log, which one can refer back to and read everything/every step taken upto now, on 
this machine. That would really be handy to trace your steps back and locate where 
some error got baked in. [COLOR="DeepSkyBlue"]Thanks for all help[/COLOR]. :-k

---

### Post by Jason_25 on 2006-05-01
All logs are in /var/log.  I don't find that technique useful because of the sheer amount of information in the logs.

---

### Post by ububaba on 2006-05-01
[QUOTE=Jason_25]All logs are in /var/log.  I don't find that very useful because of the sheer amount of information in the logs.[/QUOTE]
Thanks all the same Jason. Perhaps I can locate some of the recent foul ups.:)

---

### Post by towsonu2003 on 2006-05-01
/var/log/syslog
/var/log/messages
/var/log/auth.log

are the ones I use as my superduper log ;)

---

### Post by vruum on 2006-05-01
most of my recent foul ups are in /root/.bash_history

---

### Post by ububaba on 2006-05-01
[QUOTE=towsonu2003]/var/log/syslog
/var/log/messages
/var/log/auth.log

are the ones I use as my superduper log ;)[/QUOTE]
I have been using these directories already, my latest concern:
Is there some trick for locating "all" the files which have been accessed recently, say
a week back or a month back and they are stored in a chronological order?

---

### Post by towsonu2003 on 2006-05-01
I honestly am not sure. But try checking a few guides or howtos on the command "find". It has quite a few options on finding files base on timestamps uder select directories. Unfortunately, I can't offer help as I never used it (uhm, well, I can't even use it for a regular file search yet :) ).

---

### Post by ububaba on 2006-05-01
[QUOTE=towsonu2003]I honestly am not sure. But try checking a few guides or howtos on the command "find". It has quite a few options on finding files base on timestamps uder select directories. Unfortunately, I can't offer help as I never used it (uhm, well, I can't even use it for a regular file search yet :) ).[/QUOTE]
Well, I have been looking around. It is only, when I notice that my blood-pressure is 
getting too high, due to frustration, then I fire off a message::twisted: Some others too, 
have expressed their frustration about not find a smoother way for file search.

---

### Post by towsonu2003 on 2006-05-01
[QUOTE=ububaba]Well, I have been looking around. It is only, when I notice that my blood-pressure is 
getting too high, due to frustration, then I fire off a message::twisted: Some others too, 
have expressed their frustration about not find a smoother way for file search.[/QUOTE]
I use locate, which is extremely easy to use and so on. Well, when I need to do advanced search, I'll need to learn find :)
commands are: 
sudo updatedb (to update the search database, done in Breezy once everyday or so automatically)
locate filename

---

### Post by paritybit on 2006-05-02
gnome-find seems alright..
sudo apt-get install gnome-find
it is just a graphical frontend for find but works nicely

---

### Post by jazzgossen on 2006-05-02
"man find" will describe how to use find.

"find . -name y*" will find all files named y* in the current directory and its subdirectories

"find / -name y*" will find all files on the system named y* (although locate would be much faster to use than find in these cases)

To find files modified after a certain time, the -mmin or -mtime options should be useful.

---

