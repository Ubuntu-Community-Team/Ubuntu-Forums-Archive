---
title: "Disable lock screen on lid close"
date: 2006-01-24
forum: General Help
---

### Post by eddieave1 on 2006-01-24
I am a brand new user and would like to know how to disable lock screen on lid close?

---

### Post by Smandola on 2006-01-24
This Thread may help

[http://www.ubuntuforums.org/showthread.php?t=117654&highlight=lid](http://www.ubuntuforums.org/showthread.php?t=117654&highlight=lid)

---

### Post by eddieave1 on 2006-01-24
Thanks for your response I went into the thread and found this:

Looking around I found '/etc/acpi/lid.sh' which is called by '/etc/acpi/events/lidbtn' All that lid.sh does is blank and lock the screen.

I changed this line in 'lidbtn' from :
action=/etc/acpi/lid.sh

to this:
action=/etc/acpi/sleep.sh

Then 'sudo /etc/init.d/acpid restart' and tada!


I'm not worried about power saving features all I wanted was for the screen not to lock. 

In the 'etc/acpi/events/lidbtn' file I modified it to have no action and now my screen lid does not do anything when I like it. I am new to linux and I am happy that these forums exist.

---

