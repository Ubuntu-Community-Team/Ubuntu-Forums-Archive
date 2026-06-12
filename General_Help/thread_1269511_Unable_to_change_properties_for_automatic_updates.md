---
title: "Unable to change properties for automatic updates"
date: 2009-09-18
forum: General Help
---

### Post by chelarnens on 2009-09-18
I can't seem to change any properties for automatic updates on my newly installed Ubuntu Jaunty 9.04 (I've tried rebooting and running it both as regular user, with sudo privileges and with sudo su), but it stays the same with "check for updates: Daily" and all other options not checked, but with a round dot in it instead. Image of it can be seen here: [http://bayimg.com/EADJKAAcP]("http://bayimg.com/EADJKAAcP")
No errors are found in log files and I've tried running "sudo apt-get install --reinstall software-properties-gtk" without any improvement.

To rule out the most common permission bug in software-properties-gtk with Ubuntu 9.04 I've run:

sudo rm /var/spool/anacron/cron.daily

sudo chmod 755 /etc/cron.daily/apt

Does anyone have a suggestion on how to further investigate this issue?

*Edit* A new bug regarding this has now been reported to Launchpad:
[https://bugs.launchpad.net/bugs/434146](https://bugs.launchpad.net/bugs/434146)

---

