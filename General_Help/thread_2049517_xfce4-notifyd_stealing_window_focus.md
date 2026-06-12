---
title: "xfce4-notifyd stealing window focus"
date: 2012-08-28
forum: General Help
---

### Post by pqwoerituytrueiwoq on 2012-08-28
So i was playing [supertuxcart]("apt:supertuxcart") and sometimes when i get a email, song changes, or pidgin tell me something my [supertuxcart]("apt:supertuxcart") window looses its window focus making me crash 
i am using xfce 4.10 and compiz on xubuntu 12.04, anyone else had this happen or know a fix?

---

### Post by pqwoerituytrueiwoq on 2012-08-28
i noticed on mint 13 xfce the notify-send alerts can't be clicked closed, is this cause of mdm/lightdm?
** issues is happening in xubuntu i have not encountered it on mint 13 xfce though i am not using compiz and supertuxcart on my laptop...

---

### Post by pqwoerituytrueiwoq on 2012-09-02
After settings this like this i played the game for over a hour and did the all tracks run i also had this command run at the time i was playing to make sure it was solved
```
while [ 1 ]; do notify-send --icon=info hello world; sleep 5; done
```i f i can have it notifying me every 5 seconds and play the all track grand prix and not loose window focus it must have worked
now if there was a way to get more challenging coms... i won by over 60 points
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=223542&stc=1&d=1346565009[/IMG]

---

### Post by rystraum on 2012-09-16
For the benefit of those who lands here from outside links without an Ubuntu forums account here's the fix (based on the screenshot):

[LIST=1]
[*]Open CCSM (Compiz Config Settings Manager)
[*]Look for Window Rules
[*]In the No focus field put in: ```
class=xfce4-notifyd | type=Notification
```
[/LIST]

---

