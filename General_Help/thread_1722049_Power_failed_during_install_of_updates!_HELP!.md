---
title: "Power failed during install of updates! HELP!"
date: 2011-04-05
forum: General Help
---

### Post by Mac34288 on 2011-04-05
Hey everyone!

Total fresh noob to the forum here and I am normally one of those guys who will drive for an hour trying to find my way before stopping to ask for directions, however, not with this one. 

Here's the scoop... 

Had the update manager running this morning,  and it was in the install dpkg phase of the operation when the wonderful power grid I am on went down due to the thunderstorm we were having at the time. I was watching the update at the time the power failed and the install was not completed at the time the computer shut off.

When power came back on and I restarted the computer, the log in screen came up only showing 1 and 1/2 of the 4 accounts I have on the computer. When I clicked on the one full account showing, nothing happened. After manually powering off at the tower button, and restarting, I was able to get a log in screen that was usable to log in. I was even able to launch Firefox, although it is running extremely slow, and my audio properties will not come up and the pop down bar at the top that shows applications, places, etc, does not come down. Just overall, the whole computer does not run properly. Windows take forever to open, if at all, and forever to close, if at all, etc. Restart button does not work, etc.

Anyone have any ideas?

Is there any way to manually run update manager to re-install the parts that obviously are corrupt on the previous attempt at install?

Or, is there anyway I can revert back to the status prior to the update attempt?

Many thanks in advance! :)

Mac

---

### Post by searchfgold6789 on 2011-04-05
Now I think we all know that there is a lesson to be learned from this:
[FONT=Arial Black]Never run an update during a thunderstorm. Read a book instead.
[/FONT] So - If you have a backup, use it.
If you have none, I would recommend opening a terminal and running ```
sudo dpkg --configure -a
``` to resume where you left off.
And then just to make sure everything went well, reboot and go back into a terminal. Type ```
sudo aptitude -f dist-upgrade
```Then reboot, then open a terminal and run```
sudo apt-get update && sudo apt-get upgrade
``` I hope this helps.
 - search

---

### Post by Mac34288 on 2011-04-05
Brilliant! Thanks a million! 

And, yes... no more updates during storms, however in Florida, that's nearly all the time.
Therefore, I will be getting a battery back up system today!

Again, thanks for the help!

Mac

P.S. Not sure how to mark this as SOLVED, so if you know how feel free or I will drive around until I find it. :D

---

### Post by searchfgold6789 on 2011-04-05
On the top of this page there will be a Thread Tools menu; click on that and there will be an option to mark this thread as solved.
I'm glad I could help ;)
 - search

---

