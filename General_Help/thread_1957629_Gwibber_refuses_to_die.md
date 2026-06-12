---
title: "Gwibber refuses to die"
date: 2012-04-12
forum: General Help
---

### Post by BuddyThirteen on 2012-04-12
First up: I don't hate Gwibber, so I'm not interested in removing it, or disabling it permanently in any way.

The trouble is, sometimes it hangs and freezes up the whole system (a known bug, something about being unable to find an avatar...), and when it starts doing this, it's never just once.

So I open up the terminal and killall gwibber-service and even the daemon whose name I forgot. Trouble is, Gwibber still manages to start itself up at seemingly random times for seemingly no reason with seemingly no trigger. No, I'm not accidentally clicking on it in the messaging menu.

Is there a way to kill it for good (for the remainder of a given session) and not have it resurrect itself?
[SIZE=1]
(apparently I can't creat tags? So unless I already know the tags that exist, I'm screwed--brilliant. Wow, this place has really gone downhill, hasn't it...)[/SIZE]

---

### Post by Rodney9 on 2012-04-12
Try these ways -

[http://www.makeuseof.com/tag/6-different-ways-to-end-unresponsive-programs-in-linux/](http://www.makeuseof.com/tag/6-different-ways-to-end-unresponsive-programs-in-linux/)


Rodney

---

### Post by BuddyThirteen on 2012-04-12
Those can all successfully *kill* it, yes. But it always finds a way back :-(

---

### Post by raja.genupula on 2012-04-12
If you dont use it , you can remove it happily safely 

type this in terminal ```
sudo apt-get purge "gwibber.*"
```.
all the best.

---

### Post by BuddyThirteen on 2012-04-12
> **raja.genupula said:**
> If you dont use it , you can remove it happily safely 

type this in terminal ```
sudo apt-get purge "gwibber.*"
```.
all the best.
But I do use it, else I would've removed it ages ago. Alas :-(

---

### Post by raja.genupula on 2012-04-13
ok you can use this information to disable the Gwibber service after startung your system .

[http://askubuntu.com/questions/60686/how-do-i-prevent-gwibber-service-from-starting-automatically](http://askubuntu.com/questions/60686/how-do-i-prevent-gwibber-service-from-starting-automatically)

---

