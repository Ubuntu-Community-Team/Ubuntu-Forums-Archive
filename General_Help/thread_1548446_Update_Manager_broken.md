---
title: "Update Manager broken"
date: 2010-08-08
forum: General Help
---

### Post by ravendark82 on 2010-08-08
For the last week Update Manager has been broken. It starts up when the computer starts up but it will not do anything. The window it appears in has the title update manager, but no buttons to click on or any other information.  I used force quit to close it since it was unresponsive.

I tried using terminal to manually update everything but it keeps giving me the following errors:
Could not get lock /var/lib/dpkg/lock -open (11: Resource temporarily unavailable)
Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

So I suppose Update Manager is still running, or at least one of its processes is. So what do I do next? Do I need to cancel all processes that might be associated with Update Manager? If so what are they? Or is there something else that needs to be done?

---

### Post by davidmohammed on 2010-08-08
first question - why do you have update manager running from startup?  That is probably the cause of your issues.

to force update manager to stop running

in a terminal type

sudo killall -9 update-manager

---

### Post by ravendark82 on 2010-08-08
Update Manager kept running automatically when I started up the computer. I have no clue why it started doing it. I didn't change any of the settings.   Anyway, I did what you said and was able to run a manual update. I restarted my machine and opened up Update Manager and it appears to be working again.  So thank you for your help.

---

