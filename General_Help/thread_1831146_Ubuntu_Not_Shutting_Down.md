---
title: "Ubuntu Not Shutting Down"
date: 2011-08-23
forum: General Help
---

### Post by npntransistor on 2011-08-23
Ubuntu is not shutting down completley.  If I click on shutdown it gets to a point where there it does nothing but put the monitor in sleep mode.  If I press a key or move the mouse the monitor will wake up for about 5 seconds with a black screen and then go back to sleeping.  It only has this problem about half the time the rest of the time it does exactly as designed.  I am running Ubuntu 11.04 32 bit up-to-date.  This started when I upgraded to 11.04.  Also, I looked around the forums and internet and could not find an answer.  One other thing, not that it matters if I run ```
sudo shutdown -h now
``` it has the same problem.

---

### Post by sidzen on 2011-08-23
> **npntransistor said:**
> Ubuntu is not shutting down completley.  If I click on shutdown it gets to a point where there it does nothing but put the monitor in sleep mode.  If I press a key or move the mouse the monitor will wake up for about 5 seconds with a black screen and then go back to sleeping.  It only has this problem about half the time the rest of the time it does exactly as designed.  I am running Ubuntu 11.04 32 bit up-to-date.  This started when I upgraded to 11.04.  Also, I looked around the forums and internet and could not find an answer.  One other thing, not that it matters if I run ```
sudo shutdown -h now
``` it has the same problem.

Try (in either console or terminal) 
[PHP]sudo init 0[/PHP]

---

### Post by npntransistor on 2011-08-23
I tried ```
sudo init 0
``` three times and all three times the computer shutdown without any problems.  Since this problem seems to be intermittent I don't know that it will always work as well.

---

### Post by sidzen on 2011-08-23
Good!  It (init) should work always, because . . .

"**init** is the mother of all [processes]("http://wiki.linuxquestions.org/wiki/Process").  It is started by the [kernel]("http://wiki.linuxquestions.org/wiki/Kernel") when the system is first booted.  Init reads the file /etc/inittab and uses the information in it to start processes, [daemons]("http://en.wikipedia.org/wiki/Daemon_%28computer_software%29"), and [login]("http://wiki.linuxquestions.org/wiki/Login") prompts based on the current [runlevel]("http://wiki.linuxquestions.org/wiki/Runlevel").  If for some reason a daemon is killed, it will be respawned.

**init** is also the command to switch between [run levels"]("http://wiki.linuxquestions.org/wiki/Run_levels")

---

### Post by npntransistor on 2011-08-23
So should I always shut down using```
sudo init 0
```or what should I do?  If this is the case could it potentially corrupt files compared to the usual shutdown method?

---

### Post by loolooyyyy on 2011-08-23
> **npntransistor said:**
> So should I always shut down using```
sudo init 0
```or what should I do?  If this is the case could it potentially corrupt files compared to the usual shutdown method?

killing the mother process is not such an interesting idea, OS wont do all the checks before shutting down
some files might be delayed for being written to an external storage maybe?
i had this problem in 10.10 and upgrade to 11.0.4 fixed it

---

### Post by loolooyyyy on 2011-08-24
have a look at here:
[http://ubuntuforums.org/archive/index.php/t-1306789.html](http://ubuntuforums.org/archive/index.php/t-1306789.html)

wanted to tell you to do "sudo shutdown -h -P now" as it seems your computer shuts down but doesnt power off, i did a little search and that turned up

---

### Post by npntransistor on 2011-08-25
Thank you both for all of the information.  Today I rebooted and it did the same thing except the screen just went black and that was it.  I'm not sure if that makes any difference or not but that's what happened.

---

