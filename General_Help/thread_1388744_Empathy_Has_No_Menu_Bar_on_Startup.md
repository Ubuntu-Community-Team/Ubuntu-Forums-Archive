---
title: "Empathy Has No Menu Bar on Startup"
date: 2010-01-23
forum: General Help
---

### Post by Joseph Schwenker on 2010-01-23
I have Empathy set to start when I login, and when I turn off my computer, it is always still running.  I also usually have Evolution, Liferea, and Rhythmbox running.  All of these applications usually work fine the next day when I turn on my computer.  However, for the last few days, Empathy has been starting without a menu bar.  In one instance, Rhythmbox was also menubar-less.  Now, Empathy is always without a menu bar.  If I ever need the menu bar, I have to restart Empathy.  Can anyone tell me why this is happening?  I am unable to provide a terminal output since this application starts up with my computer.  I have provided a screenshot of Empathy.  I think I have a faint idea of why Empathy is without a menu bar.  I read something somewhere about an XML file that contained the menu bar contents.  I think that since I shut off my computer without closing these applications, that file has been corrupted.  I have no idea why everything works fine once I restart Empathy, though.  If you cannot answer this question, perhaps you could tell me if it is safe to shutdown Ubuntu with applications still running.  In OS X, it will automatically tell your applications to quit safely, then turn of the computer.  I hope Ubuntu doesn't just force quit any open applications.  I am using Ubuntu 9.04 32 bit with the latest updates.  I am using Empathy 2.26.1.  Thanks!

---

### Post by Joseph Schwenker on 2010-01-30
Bump, I finally got globalmenu working today, and when I go to Empathy, the menu bar does not appear in the globalmenu nor in Empathy until I restart it.

---

### Post by Ocean Machine on 2010-03-07
Any luck with this? I've run into the same problem...

---

### Post by Joseph Schwenker on 2010-03-07
Sorry, but I haven't had any luck.  My computer crashed a month and two weeks ago, so that has pretty much put a stop to any troubleshooting.

---

### Post by Joseph Schwenker on 2010-03-20
I am still experiencing the exact same problem now, on my parents' computer.  Does anyone have any ideas?

---

### Post by labinnsw on 2010-06-21
> **Joseph Schwenker said:**
> If I ever need the menu bar, I have to restart Empathy.

I don't quite remember the reason why this happens but it was mentioned in a conky solution some time ago. In the bit I have quoted lies the symptom necessary to diagnose the problem. The treatment is:

1. Save this script in your home directory as .empathy_start.sh```
#!/bin/bash
sleep 10
killall empathy &
sleep 30
empathy
```
2. Change the Startup Applications command to point to the script.
3. Make the script executable. (right click >> properties >> permissions)
4. One reboot will reveal that your Empathy is cured.

---

### Post by Joseph Schwenker on 2010-06-21
Thanks a bunch for that!  When I start my computer tomorrow, I'll see if it works.  Thanks for contributing your solution.

---

### Post by Joseph Schwenker on 2010-06-26
Hmm... it seems to work, but the other problem is appearing when I use the script; the contact list is blank, and changing my status from the dropdown does nothing.

---

### Post by labinnsw on 2010-06-26
> **Joseph Schwenker said:**
> Hmm... it seems to work, but the other problem is appearing when I use the script; the contact list is blank, and changing my status from the dropdown does nothing.

Are your chat accounts still there?

---

### Post by Joseph Schwenker on 2010-06-26
No.  The contact list is completely blank.

---

### Post by labinnsw on 2010-06-26
It seems as if at some point your config file was deleted. You can recreate it by setting up you accounts again.

---

### Post by Joseph Schwenker on 2010-06-26
I've had this problem in every single install of Ubuntu that I've had, from 9.04 on.  I doubt that recreating the configuration will change anything; it'll just be deleted again.  Besides, if I restart Empathy, the list comes back.  It's a graphical problem or incompatibility, not a problem with the configuration.

---

### Post by labinnsw on 2010-06-27
> **Joseph Schwenker said:**
> Besides, if I restart Empathy, the list comes back.If that is the case, the application is still loading too quickly. Add 5 seconds to the sleep times and keep adjusting until it works as it should.

---

