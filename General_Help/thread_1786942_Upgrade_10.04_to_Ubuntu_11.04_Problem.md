---
title: "Upgrade 10.04 to Ubuntu 11.04 Problem"
date: 2011-06-20
forum: General Help
---

### Post by xzin101 on 2011-06-20
hey,
i was trying to upgrade from 10.04 to 11.04 and during the upgrading process, the operation got interrupted and there was an error due to reading file, so i had to restart the upgrading process, but once i restarted..i couldn't see the [UPGRADE] Option anymore!! instead there were 3 options and one of them says to Reinstall Ubuntu 11.04 !! and that it's gonna delete all the files [pictures, movies, music ... etc!!] which were already there on Ubuntu 10.04!! so am confused now! what should i do i can't afford losing my data! and i can't boot to ubuntu 10.04 anymore either...so PLZ HELP! :(

---

### Post by Jerry N on 2011-06-20
No problem - just reinstall your files from your backups.  You do have backups don't you?

If you can't boot your OS, you could use a 11.04 live CD or something like Puppy Linux to access the files on the disk and **CREATE BACKUPS** of your files.

---

### Post by xzin101 on 2011-06-20
So, I understand from you that this option will actually DELETE all my Ubuntu 10.04 data??! 
If yes, then i don't get how Ubuntu developers haven't really thought about that?!!!

---

### Post by FormatSeize on 2011-06-20
> **xzin101 said:**
> So, I understand from you that this option will actually DELETE all my Ubuntu 10.04 data??! 
If yes, then i don't get how Ubuntu developers haven't really thought about that?!!!
A reinstallation will probably involve wiping your hard disk. You really should have backups.
As for the developers thinking of that, it seems like it would be impossible for them to account for something that happens at random.

---

### Post by psusi on 2011-06-20
Choose manual partitioning and do NOT check the format box and your files should be left alone.

---

### Post by galvatron408 on 2011-06-20
Wait, how could anyone blame the developers? I think the ubuntu developers have created one of the best open source free linux distro.

You should try upgrading Red Hat Linux. Wait, another problem there. Red Hat says that it's better to reinstall. That means, their upgrade process is.... backup your files, install the latest version and restore your files.

---

### Post by pqwoerituytrueiwoq on 2011-06-20
fire up a live cd and copy your files to a flash drive
then you can reinstall 11.04 but i suggest you try it on a live cd 1st i am sticking with the lts 10.04

---

### Post by Slim Odds on 2011-06-20
There is NO direct upgrade path from 10.04 to 11.04. Were you upgrading to 10.10 when this happened? or from 10.10 to 11.04?

Most upgrade processes (for any OS or software) don't like to get interrupted. It can always cause major problems.

---

### Post by psusi on 2011-06-20
> **Slim Odds said:**
> There is NO direct upgrade path from 10.04 to 11.04. Were you upgrading to 10.10 when this happened? or from 10.10 to 11.04?

Most upgrade processes (for any OS or software) don't like to get interrupted. It can always cause major problems.

My guess is that he booted the 11.04 livecd and used the new option to do a clean install, replacing the existing install.  Technically it is replace rather than upgrade.

---

### Post by leo_m on 2011-06-30
Why is there no direct upgrade path from 10.04 to 11.04 when all x.04 releases are LTS and /etc/update-manager/release-upgrades allows you to specify a prompt=lts?

I cannot figure out why one cannot upgrade from LTS to LTS...can someone please clarify if this is supported or not?

---

### Post by hawthornso23 on 2011-06-30
11.04 isn't LTS.  The "04" just means it was released in april.

---

### Post by Slim Odds on 2011-06-30
> **hawthornso23 said:**
> 11.04 isn't LTS.  The "04" just means it was released in april.

Yes, LTS releases come every TWO years... not every year.

---

