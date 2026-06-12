---
title: "2 Quick (I think) Problems"
date: 2012-03-09
forum: General Help
---

### Post by OldManRiver on 2012-03-09
All,

Have 2 quick problems:
[LIST=1]
[*]Synaptic Not Working
[*]phpMyAdmin IP setup for Sync
[/LIST]

**Synaptic Not Working**
I ran:
   apt-get remove synaptic
and
   apt-get install synaptic
but no change.  It shows up starting to open and then just goes away!

**phpMyAdmin IP setup for Sync**
99.9% of the time, I'm just fine with PHP code using localhost on supported host.

Saw this new sync feature in phpMyAdmin, when source upgraded, but it forces be to define non-localhost sessions and instead need the IP. This however is problematic as:

Ex:
Host: 192.168.1.2:3306
UID: myuser
PWD: mypass

Always says "Access denied for user myuser@192.16.1.2 with password=YES"

I looked for HOWTOs and one says define a new user in the remote DB of myuser with host 192.168.1.2, but this does not work.

Been testing both with phpMyAdmin and with MySQL Administrator, but no luck on either.

My config is 2 Ubuntu boxes and 1 WinXP laptop. Trying to sync all 3.

Starting with U-Box to U-Box as that should be the easiest.

Will appreciate all help on this!

Thanks!

---

### Post by oldos2er on 2012-03-09
> **OldManRiver said:**
> 
Synaptic Not Working


Can you run ```
sudo apt-get update && sudo apt-get upgrade
``` in a terminal and post the output here?

---

### Post by jerrrys on 2012-03-09
gksudo synaptic ?

---

### Post by OldManRiver on 2012-03-13
> **oldos2er said:**
> Can you run ```
sudo apt-get update && sudo apt-get upgrade
``` in a terminal and post the output here?

oldos2er,

No way in Hell, Never upgrading until the next LTS version is officially released and never suggest that to anyone, because only LTS versions are stable!

OMR

---

### Post by OldManRiver on 2012-03-13
> **jerrrys said:**
> gksudo synaptic ?
Same results as clicking on it, opens momentaritly then closes.  Can see it come up in "System Monitor" and then go away!

---

### Post by oldos2er on 2012-03-13
> **OldManRiver said:**
> oldos2er,

No way in Hell, Never upgrading until the next LTS version is officially released and never suggest that to anyone, because only LTS versions are stable!

OMR

*sudo apt-get upgrade* does not upgrade you to a new version Of Ubuntu, it only installs package upgrades for the version you're already running.

I asked to see the output of it because it aids troubleshooting.

---

### Post by jerrrys on 2012-03-13
check to be sure your in sudo-mode

[ATTACH]214267[/ATTACH]

---

### Post by OldManRiver on 2012-03-14
> **oldos2er said:**
> *sudo apt-get upgrade* does not upgrade you to a new version Of Ubuntu, it only installs package upgrades for the version you're already running.

I asked to see the output of it because it aids troubleshooting.
Ann,

No "apt-get update" does what you say, "apt-get upgrade" updates your version!

Been doing Ubuntu for over 5 years, think I started with 6.04, so know the difference in these 2 commands!

Cheers!

OMR

---

### Post by OldManRiver on 2012-03-14
> **jerrrys said:**
> check to be sure your in sudo-mode

[ATTACH]214267[/ATTACH]
Jerrys,

Thanks! but that is what I already have, so not that!

Cheers!

OMR

---

### Post by Zill on 2012-03-14
> **OldManRiver said:**
> Ann,

No "apt-get update" does what you say, "apt-get upgrade" updates your version!
I hate to disagree but my understanding is that "apt-get upgrade" only upgrades *specific* packages - not the entire distro to a new release.

According to the Ubuntu [AptGetHowto]("https://help.ubuntu.com/community/AptGet/Howto"), Maintenance commands section, "apt-get update" should be run periodically to make sure your sources list is up-to-date.  This is the equivalent of "Reload" in Synaptic.

"apt-get upgrade" upgrades all installed packages. This is the equivalent of "Mark all upgrades" in Synaptic.

However, as this only "upgrades" packages in accordance with the release defined in your /etc/apt/sources.list, this means that packages will *only* be upgraded to the latest version *appropriate for that Ubuntu release*.  This does *not* mean that the entire Ubuntu OS is upgraded to a new release.

It is good practice to run "sudo apt-get update", followed by "sudo apt-get upgrade", on a regular basis to minimise bugs in your system.  Of course, both the Update Manager and Synaptic can do this if you prefer a GUI.

Note for newbies:  the two commands above should have the "sudo" prefix as these are system-wide commands requiring admin privileges.

---

### Post by oldos2er on 2012-03-14
> **OldManRiver said:**
> Ann,

No "apt-get update" does what you say, "apt-get upgrade" updates your version!

Been doing Ubuntu for over 5 years, think I started with 6.04, so know the difference in these 2 commands!

Cheers!

OMR

```
man apt-get
``` should clear things up. *apt-get update* refreshes the package lists. *apt-get upgrade* "is used to install the newest versions of all packages currently installed on the
system from the sources enumerated in /etc/apt/sources.list."

If you read the forums you'll see these output from these commands is very frequently requested.

---

### Post by OldManRiver on 2012-04-02
All,

First Q solved!

Had nothing to do with updates or upgrades, dpkg had corrupted itself from one of the updates or upgrades, so had to purge dpkg and re-install.  Course synaptic is not going to work, since it totally relies on dpkg.

Back to the 2nd Q:

phpMyAdmin IP setup for Sync

Never saw anyone chime in on this.

Cheers!

OMR

---

### Post by OldManRiver on 2012-06-08
All,

Reviewing all my "OPEN" threads and trying to "CLOSE" them and get them solved.  

I'm numbering them.  This is Thread #15 in my series.

Your help in getting them resolved, closed, SOLVED, is appreciated!

OMR

---

### Post by Zill on 2012-06-08
> **OldManRiver said:**
> ...Your help in getting them resolved, closed, SOLVED, is appreciated!
Sorry but I find this post ambiguous!

Do you still need help?  If so then please respond to any questions that have been posted in this thread.

If your problem has been resolved then please use the "Thread Tools" at the top to mark the thread as "Solved".

---

