---
title: "Time Sync Messing Up"
date: 2006-04-10
forum: General Help
---

### Post by MightyTuna on 2006-04-10
I'm running breezy badger in an Active Directory Domain and I need the machine to run "net time set" at boot up and hourly in cron to keep the tyme syncronized to the domain's time.  Unfortunately my scripts don't seem to be working.

I don't care if the machine syncs with an Internet server initially, but I need the last thing it does at bootup to be "net time set"

I have two scripts, both of which are set to allow world read and world execute:
/etc/init.d/local looks like this
#!/bin/sh

net time set

and /etc/cron.hourly/nettime.sh looks like this
#!/bin/sh

net time set


what am I doing wrong?

---

### Post by dcstar on 2006-04-10
[QUOTE=MightyTuna]I'm running breezy badger in an Active Directory Domain and I need the machine to run "net time set" at boot up and hourly in cron to keep the tyme syncronized to the domain's time.  Unfortunately my scripts don't seem to be working.

I don't care if the machine syncs with an Internet server initially, but I need the last thing it does at bootup to be "net time set"

I have two scripts, both of which are set to allow world read and world execute:
/etc/init.d/local looks like this
#!/bin/sh

net time set

and /etc/cron.hourly/nettime.sh looks like this
#!/bin/sh

net time set


what am I doing wrong?[/QUOTE]

Try putting the full path name to the net executable (/usr/bin/net on my system).

---

