---
title: "Server Brute Forced - Scripts running | Help?"
date: 2011-05-04
forum: General Help
---

### Post by ondemanddesign on 2011-05-04
Hello, my server was allowing an open connection from ssh (I know, bad). It was brute force hacked (poor password, changed now). Now every time I remove ip's from the hosts.deny file and save they are added to the file again within seconds. I have checked crontab and init.d and could not find the script running. How do I find those pesky scripts and kill them?

---

### Post by lithopsian on 2011-05-04
cron scripts run from quite a few places.  You'll have to check them all.  The breakin probably installed a rootkit of some sort, which you'll have to search for buried under the home directory of whoever they broke in as (root?).  It most likely also replaced a number of system binaries with trojans, any one of which can refresh others that you might have fixed.  It is a significant piece of work to manually fix all these issues, although it can certainly be done.  Less experienced, or more busy, people might just want to wipe and reinstall.  The auth log file might give you some clues asa to what was actually installed during the breakin although this is sometimes wiped.

---

