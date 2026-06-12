---
title: "I never want my computer to suspend or go to sleep, but it does"
date: 2006-06-10
forum: General Help
---

### Post by ryharv on 2006-06-10
Hi all,

I have a problem with Ubuntu 6.06 going to sleep after a while.  I used to use 5.10 and this never happened.  I am not logged in as myself, so I am not using the desktop software.  But I am running a long rsync job from another computer via the terminal/SSH.  The rsync stops every 30 minutes or so because my Ubuntu box is falling asleep.  Anybody know how to disable this sleep feature?  Again, not in the desktop, but beneath that.

Thanks,

  Ryan

---

### Post by Skye on 2006-06-10
This is a **completely untested** guess, so use at your own risk.  

I think you could rename /etc/acpi/sleep.sh to /etc/acpi/sleepBKUP.sh, and the lack of an executable would prevent the system from suceeding in sleeping.

This is completely inelegant, though- I'm sure someone has a better idea.

---

### Post by ryharv on 2006-06-11
Thank you for the suggestion, but it didn't work.  I renamed all of the "sleep" and "hibernate" files in /etc/acpi but it's still going to sleep.  Anybody know where there is a configuration file that sets the time until sleep?  Maybe I can configure it to wait a very long time before sleeping.

---

### Post by _simon_ on 2006-06-11
Try this:

From terminal type: gconf-editor

Then go to apps -> gnome-power-manager

There's a whole series of options in there to fiddle with - see my screenshot

---

