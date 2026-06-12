---
title: "Repositories not working"
date: 2011-11-26
forum: General Help
---

### Post by csevcik on 2011-11-26
What's going on with the Ubuntu repositories? 4 Machines are unable to connect to some of the. Neither Oneiric nor Natty are working. Both 32 bits and 62 bits fail 

ubuntu natty-getdeb apps
ubuntu natty-getdeb games
ubuntu oneiric-getdeb apps
ubuntu oneiric-getdeb games

fail. It does not help to change the repository server.

The repositories seem to be off line, the problem started yesterday 11/25/2011.

---

### Post by drs305 on 2011-11-26
When I visit the site and click on Natty, I get this message in bold red:
> WARNING: all packages have been deleted from this repository 
It's the same for the other releases as well.

[http://www.ubuntuupdates.org/ppa/getdeb_apps?dist=natty]("http://www.ubuntuupdates.org/ppa/getdeb_apps?dist=natty")

I didn't see an explanation on the site, though perhaps an explanation will be forthcoming.

---

### Post by bluexrider on 2011-11-26
UbuntuUpdates arbitrarely picked ubuntu-tweak as the main package of this PPA.
      
Package     Release     Latest Version     Latest Update              
**[ubuntu-tweak]("http://www.ubuntuupdates.org/packages/show/369607")**         oneiric         *DELETED*         2011-11-25 05:04:34 UTC                   
**[ubuntu-tweak]("http://www.ubuntuupdates.org/packages/show/307694")**         natty         *DELETED*         2011-11-25 05:04:32 UTC                   
**[ubuntu-tweak]("http://www.ubuntuupdates.org/packages/show/254057")**         maverick         *DELETED*         2011-11-25 05:04:20 UTC                   
**[ubuntu-tweak]("http://www.ubuntuupdates.org/packages/show/198029")**         lucid         *DELETED*         2011-11-25 05:04:23 UTC

Don't know but somethings going on.....

---

### Post by vexorian on 2011-11-26
Wow, I actually just noticed this and was googling for an answer, didn't expect goog to index this thread and the last reply so quickly.

---

### Post by LinuxFan999 on 2011-11-26
I just visited the site to re-confirm this issue.

---

### Post by oldtimer7777 on 2011-11-26
> **LinuxFan999 said:**
> I just visited the site to re-confirm this issue.

I never use GetDeb to install..  Why don't you use the actual PPAs to install what you want on your system?   It is better that way too.

---

### Post by vexorian on 2011-11-28
It seems to have been a small bug that fixed itself.

GetDeb games is a PPA now. Also, some games don't have their own PPAs yet.

---

