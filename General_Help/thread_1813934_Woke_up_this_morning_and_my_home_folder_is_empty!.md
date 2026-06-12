---
title: "Woke up this morning and my home folder is empty!"
date: 2011-07-28
forum: General Help
---

### Post by kevcoder on 2011-07-28
I get up this morning, turn on the monitor and find that my home folder (/home/dev) is now empty except for two folders(Desktop and Downloads) which are themselves empty.

Strangely I found the install folder for Aptana, intact, moved into the root of the folder set up as my samba share.

The last thing I did was to apply all of the important security updates (I've disabled all others in).

I was also playing around with a bash script trying to mass convert wma files to mp3 with ffmpeg.  That failed and I deleted the 48 mp3 files it created.  Those are the only files in the trash.


**Is there some sort of log of all actions on a linux system that I can review that would show all deletes, moves, etc???**

---

### Post by fdrake on 2011-07-28
well there is 

```
history
```
shows all the commands you typed in the terminal

```
less /var/log/messages
```
view general log file

you said /home/dev? do you have a user named dev?

do you mount you /home/dev externally or is saved in the same partition of the "/" root system?

---

