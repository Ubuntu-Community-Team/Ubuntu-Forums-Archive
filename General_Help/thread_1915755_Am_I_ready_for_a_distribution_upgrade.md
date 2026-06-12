---
title: "Am I ready for a distribution upgrade?"
date: 2012-01-26
forum: General Help
---

### Post by asuastrophysics on 2012-01-26
Hey guys,

Some of the new stuff in Ubuntu looks really cool, and I think I want to upgrade from 10.10 to 11.04. Besides making a backup of everything, is there anyway of "preparing" for the upgrade? That is, are there any steps I can take to help insure the most successful upgrade? You guys know how upgrades are ;)
Any ideas?

---

### Post by xyzzyman on 2012-01-26
12.04 is still in Alpha 1 stage. If you aren't prepared for random system breakage and lots of troubleshooting, and possibly having to reinstall you should wait.

[https://wiki.ubuntu.com/PrecisePangolin/ReleaseSchedule?action=show&redirect=PreciseReleaseSchedule](https://wiki.ubuntu.com/PrecisePangolin/ReleaseSchedule?action=show&redirect=PreciseReleaseSchedule)

---

### Post by asuastrophysics on 2012-01-26
> **xyzzyman said:**
> 12.04 is still in Alpha 1 stage. If you aren't prepared for random system breakage and lots of troubleshooting, and possibly having to reinstall you should wait.

[https://wiki.ubuntu.com/PrecisePangolin/ReleaseSchedule?action=show&redirect=PreciseReleaseSchedule](https://wiki.ubuntu.com/PrecisePangolin/ReleaseSchedule?action=show&redirect=PreciseReleaseSchedule)

Sorry, I changed my post to reflect that. 12.04 -> Changed to 11.04. You're definitely right about 12.04, but how should I prepare for my upgrade to 11.04? Anything I can do?

---

### Post by xyzzyman on 2012-01-26
> **asuastrophysics said:**
> Sorry, I changed my post to reflect that. 12.04 -> Changed to 11.04. You're definitely right about 12.04, but how should I prepare for my upgrade to 11.04? Anything I can do?

11.04 was a big change from 10.10 because of unity. You'll have responses to just do a fresh install, but I think the best way of thinking is to be prepared to do a fresh install. If you wind up liking Unity, then maybe just do the upgrade to 11.04 or even 11.10 for now, and then do a fresh install of Ubuntu 12.04 in a few months when it comes out, as it's an LTS so stability has been a major focus during development.

---

### Post by snowpine on 2012-01-26
[Ubuntu Upgrade Notes]("https://help.ubuntu.com/community/UpgradeNotes") has some good suggestions including:

Back up all your data

Read the pros and cons of upgrade vs. fresh install

Thoroughly test a Live CD of the new release

---

### Post by jorpoveda on 2012-01-26
Yes I was wondering the same thing. Is there a way to have a Bluetooth HDD and an app that wiressly is backing up my file on Ubuntu? I have been looking but I dont seem to find it.

---

### Post by asuastrophysics on 2012-01-26
I guess I was thinking more along the lines of "preparing" for the upgrade by making sure that the directory permissions are exactly as they should be. Thanks for all of the advice so far though!

---

### Post by xyzzyman on 2012-01-26
> **asuastrophysics said:**
> I guess I was thinking more along the lines of "preparing" for the upgrade by making sure that the directory permissions are exactly as they should be. Thanks for all of the advice so far though!

The only thing you can do beside current backup is purge any PPA's if you've added them:

[http://www.webupd8.org/2010/08/ppa-purge-added-to-official-ubuntu-1010.html](http://www.webupd8.org/2010/08/ppa-purge-added-to-official-ubuntu-1010.html)

---

### Post by snowpine on 2012-01-26
> **asuastrophysics said:**
> I guess I was thinking more along the lines of "preparing" for the upgrade by making sure that the directory permissions are exactly as they should be. Thanks for all of the advice so far though!

Have you modified your directory permissions? If not, then they should be "exactly as they should be." :)

---

### Post by asuastrophysics on 2012-01-27
> **snowpine said:**
> Have you modified your directory permissions? If not, then they should be "exactly as they should be." :)

Unix-like OS's are weird! :o
I think directory permissions can sometimes change when some programs are given root access. Take Mac OS X for example. OS X ships with a "Disk Utility" program that can repair permissions on the partition. If you click "Repair Permissions" after many weeks of computer use, you'll get quite a long list of differing permissions in the activity log. :-?

I don't know if Linux suffers from this as well, but OS X and Linux do share similar folder hierarchies, since part of OS X's "DNA" comes from NextStep, which was a Unix-like OS. (both have /bin, /etc, /var, /usr, etc.)

EDIT: I found this link which explains more about how disk permissions can progressively change over time :D
[http://superuser.com/questions/288808/how-do-disk-permissions-fall-into-a-state-of-disrepair](http://superuser.com/questions/288808/how-do-disk-permissions-fall-into-a-state-of-disrepair)

---

### Post by snowpine on 2012-01-27
Linux gives you unlimited freedom, including the freedom to create your own permission problems if you choose. :) The recommended method to gain root access without accidentally changing permissions is described here: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

Short version: Conduct your daily business as a normal user and escalate to root privileges only when necessary. Use 'sudo' for terminal apps or 'gksu' for GUI apps. Everyday documents/files go in your home folder (where you are the owner) and everyday work/school/play tasks do not require sudo/gksu.

ps I do not think you need to worry about any problems with OSX. :)

---

### Post by pme 72 on 2012-01-28
If you activated any proprietary drivers for your video chip set/card you can avoid potential incompatibility issues by disabling them prior to running the upgrade.

---

### Post by critin on 2012-01-28
> That is, are there any steps I can take to help insure the most successful upgrade?

If you normally run wireless, I suggest adding an ethernet wire for this job.

---

