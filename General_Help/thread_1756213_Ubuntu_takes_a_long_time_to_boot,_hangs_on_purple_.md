---
title: "Ubuntu takes a long time to boot, hangs on purple screen."
date: 2011-05-12
forum: General Help
---

### Post by marmaladejackson on 2011-05-12
Hi All,

This evening I was playing around with some settings.  I upgraded to 11.04 this weekend and haven't had much time to play with it.  I turned off Unity right away as I found it difficult to navigate and didn't have time to experiment.  To night, decided to give it another chance and enabled it via CCSM.  After fiddeling for a few minutes, decided I still didn't like it all that much and disabled it via CCSM.  Lost all my window decorations so I decided to log out then log back  in to reset the desk top.  Moved the mouse a bit too quick and selected "hibernate" instead.  Couldn't get the system to wake back up so just hit a hard reset and this is where the problem started.

The system booted passed the post as normal and got to that Barney purple screen and stopped.  No splash or anything.  I waited about 5 minutes and reset again.  This time after the POST I noticed that the optical lit up then after a few seconds went dark.  I hit the NumLock to see if the key board was frozen and I heard the hard drives spin up and the boot process continued.  I got an error message that flashed across the screen too quick to read and I found my self in the log on sessions screen as normal.  I tried restarting a couple of times and the same thing happens ever time:

-POST
-Purple screen  
-Hit NumLock
-Error message
-Boots normal

I attached a photo of the error message, its a bit blurry as I didn't grab my camera quickly enough.  If anyone wants a better shot I can certainly try again or video the entire boot.

Anybody have any ideas?

Thanks 
Brian

---

### Post by Sef on 2011-05-12
> I attached a photo of the error message, its a bit blurry as I didn't grab my camera quickly enough. If anyone wants a better shot I can certainly try again or video the entire boot.

A better picture would be good. It is impossible to read the error message.

---

### Post by marmaladejackson on 2011-05-12
OK, I took a [1 minute video]("https://docs.google.com/leaf?id=0B86uQLhrp6jyMmE0ODVhNmUtMGY5YS00YTMwLTg4YmYtNTQxODM2ODYzNjQz&hl=en&authkey=CLvs6oIP") of the boot process.  The error message says:

.... *Starting AppArmor profiles [OK]
*Setting sensors limits use [OK]
/etc/rcS.d/S50oss4-base: line 21: $'\302\240exit' : command not found [failed]
*Starting Open Sound System

Does that help?

Thanks again!
Brian

---

### Post by jerrrys on 2011-05-13
[http://ubuntuforums.org/showthread.php?t=1756110](http://ubuntuforums.org/showthread.php?t=1756110)

---

### Post by marmaladejackson on 2011-05-13
Thanks jerrrys... I subscribed to the launch pad.  Maybe it'll be fixed with a kernel update.

-B

---

