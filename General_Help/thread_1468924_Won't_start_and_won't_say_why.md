---
title: "Won't start and won't say why"
date: 2010-05-01
forum: General Help
---

### Post by AngusM on 2010-05-01
I have Ubuntu 10.04 and it freezes on start, and gives little clue as to why. If I push escape, the purple screen disappears, and I see a lot of:

udevd[302]: SYSFS{}= will be removed in future blah blah blah\
But that looks like a warning not an error. 
Then I see a few
init: ureadadhead-other main process (628) terminated with status 4
but I read that that's perfectly safe.

Later on it's 
Skipping profile in /etc/apparmor.d/disable: usr.bin.firefox3-5
Warning: found usr.sbin.ntpd in /etc/apparmor.d/force-complain, forcing complain mode

Rather than invoking init scripts through /etc /init.d usr the service(8)

Since the script you are attempting to invoke has been converted to an
Upstart blah blah blah....

Then it gives a bunch of messages that don't seem very important until 
* Checking battery state...            [ OK ]

Sorry, but there's pretty well nothing else that it gives me. I tried using the Ubuntu Rescue Remix CD, but all that gives me is a command-line, and I have no idea what to do w/it. How do I proceed?

---

### Post by DawieS on 2010-05-01
Have you checked the **md5sum** of your ISO download against the official server/mirror?

I was unable to complete a torrent download, and was spammed with garbage. I eventually reverted to http download.

---

