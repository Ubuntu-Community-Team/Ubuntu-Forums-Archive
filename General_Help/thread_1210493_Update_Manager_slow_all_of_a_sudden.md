---
title: "Update Manager slow all of a sudden"
date: 2009-07-11
forum: General Help
---

### Post by Finalfantasykid on 2009-07-11
[http://www.youtube.com/watch?v=0zKr2cZ1JRE](http://www.youtube.com/watch?v=0zKr2cZ1JRE)

It was working fine the other day, but now whenever it updates, it hangs or something for about a minute. It used to take just seconds.

I am using 9.04 by the way.

EDIT: I have tried...

-Changing servers
-sudo apt-get upgrade
-going to synaptic package manager and marking update-manager for reinstallation>applied

No success with any of these...

---

### Post by earthpigg on 2009-07-11
have you tried changing the server it connects to?

system -> admin -> software sources -> download from -> other -> select best server

---

### Post by Finalfantasykid on 2009-07-11
Ya that was one of the first things I tried.  I changed it to the Ubuntu main server, but same problem.  I switched back to the Canada Sever, and same problem.

*Updates first post with things I have tried to fix this*

---

### Post by SartoriusGenuflectus on 2009-07-11
I have just today upgraded from 7.10 to 8.04 (Hardy) and update manager is hanging. Can't access System/ Administration / Software Sources: System Administration icon appears on desktop but never opens.
System monitor is showing the Update Manage process as sleeping with zero CPU usage and about53Mb of memory.
This is what I have been doing:
===========================================================================
upgrade to 8.04 LTS
===========================================================================
Opened Update Manager
647 updates available as well as new release 8.04 LTS
[Upgrade]
The upgrade aborts now. Your system could be in an unusable state. A recovery will run now (dpkg --configure -a).
Opened Update Manager
Declined partial upgrade
[Check]
[Install upgrades]
In alsa configuration, I accepted new version of configuration file
Restarted computer
System /Administration/ System Monitor now shows Ubunut release as 8.04 Hardy
Opened Update Manager
New release 8.10 is available
Got error: Not all updates can be installed
chose [Close]
Click on [Check] cause hang as update manager goes to sleep
Ended Update-manager process with System-monitor
Restarted computer
Opened update Manager
Chose [Partial upgrade]
Update manager aborted without apparantly doing anything
Re-Opened update Manager
Chose [Partial upgrade]
Update manager aborted without apparantly doing anything

Re-Opened update Manager
Chose 8.10 [UPgrade]
Downloaded a couple of files quickly then update manager aborted

---

### Post by Finalfantasykid on 2009-07-11
Ok So I'm pretty sure that I fixed it.  Now it only takes a few seconds to complete.

For anyone else having this problem, this is what I did.
---

Perhaps I should have said that I did a "sudo apt-get install kubuntu-desktop" and "sudo apt-get install xubuntu-desktop" just to try them out.  After I was done playing around with them I followed [http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome) to get rid of the desktops.  This worked, however it seems like it left behind a bunch of ophaned packages and other crap.  So whenever I went to check for updates, it probably had to go through 3 or so times more packages.  

So I deleted the orphaned packages using gtkorphan, and then I went to synaptic package manager, and deleted all residual packages, and then did "sudo apt-get autoclean" , "sudo apt-get clean" , "sudo apt-get autoremove".  And now it goes way faster :)

---

### Post by Gizenshya on 2009-07-11
sweet.  I just cleared up a couple gigs with hat :)

---

