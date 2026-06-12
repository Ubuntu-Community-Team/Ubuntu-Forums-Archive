---
title: "gnome-schedule time setting problem"
date: 2009-07-22
forum: General Help
---

### Post by ajgreeny on 2009-07-22
I have been trying to use gnome-schedule to set a recording of web radio using a shell script.  The script works with no problem at all, but I am totally unable to set any times in gnome-schedule; all the time drop-down boxes just simply go back to the present time when I move to the next box, which of course makes the program absolutely no use at all.

I have found a launchpad bug noted [https://bugs.launchpad.net/ubuntu/+source/gnome-schedule/+bug/346937](https://bugs.launchpad.net/ubuntu/+source/gnome-schedule/+bug/346937), but there is no apparent follow up to that, and I wonder if anyone has any idea what the problem might be with this.

EDIT:
OK, I found the problem after a long search of launchpad.
To overcome the problem of time setting not being possible, just open /usr/share/gnome-schedule/gnome-schedule.glade with root privileges and search for and replace all instances of "10 10" with "0 0", without the quote marks, of course.  Restart gnome-schedule and it works properly again.

---

