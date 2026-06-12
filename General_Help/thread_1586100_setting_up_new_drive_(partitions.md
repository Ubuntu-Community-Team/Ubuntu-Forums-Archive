---
title: "setting up new drive (partitions"
date: 2010-10-01
forum: General Help
---

### Post by spiky001 on 2010-10-01
Ok I have a drive I set up as follows 20 gig root 1gig swap 19gig usr. Now I want to make the partition usr, a user account, I created a new user but that puts it in the root partition, is there a way to move the new user account to the usr partition or should I reinstall which is no prob (fresh install)

---

### Post by psusi on 2010-10-01
Users home directories go in /home, not /usr.  /usr is for various parts of the OS.

---

### Post by spiky001 on 2010-10-01
so best option to delete partition then format ext3 then how to make that a user home?

---

### Post by psusi on 2010-10-01
If you delete it you will be loosing half your OS.  You need to reinstall and use that partition for /home this time, not /usr.

Though why do you even want to have a separate partition?  It isn't worth the bother imho.  Eventually you will probably fill up /home and be upset that you still have 10 gigs free in / that you can't use.

---

### Post by spiky001 on 2010-10-01
ok thks for info will reinstall

---

### Post by srs5694 on 2010-10-01
IMHO, a separate /home partition *is* worth having. The catch is that, with only 40GB of space, you'll have to be more careful about deciding how much to allocate to root (/) vs. /home than if you had, say, 500GB of space available. On that amount of space, I'd probably give 15GB to root (/) rather than 20GB, but it really depends on how many programs you want to install vs. how much user data you want to store.

---

### Post by psusi on 2010-10-01
> **srs5694 said:**
> IMHO, a separate /home partition *is* worth having.

Why?  The usual reason given is so that you can reinstall the OS and keep your personal files, but you can do that without having it on a separate partition; just don't choose to format the partition when you reinstall.

---

### Post by spiky001 on 2010-10-02
It has bt4 on as sdb system takes quite a bit so I split it this way. As normally it is run as root so I decided to add a user leaning to safety side and yes if I find it wrong I can change it

---

### Post by srs5694 on 2010-10-02
> **psusi said:**
> [quote=srs5694]IMHO, a separate /home partition *is* worth having.Why?  The usual reason given is so that you can reinstall the OS and keep your personal files, but you can do that without having it on a separate partition; just don't choose to format the partition when you reinstall.[/QUOTE]

That only works if you're re-installing or upgrading the same OS version and if the original installation is in working condition. With a separate /home partition, you can switch to a different distribution entirely, downgrade to an earlier version, or wipe the root (/) filesystem and re-install if the main installation has become hopelessly corrupted. Furthermore, my experience with in-place upgrades is mixed; they often work, but they also often create problems -- some packages may not work correctly or the whole thing sometimes refuses to boot. Thus, I often prefer to wipe the disk and re-install, or install a new distribution version side-by-side with the old one for a test period, rather than upgrade directly.

There are other advantages to having a separate /home partition, too, such as keeping the personal data safe from damage should a filesystem problem corrupt another filesystem; using different low-level filesystems to improve performance; using whole-partition backup tools and keeping user and system data separate; and sharing /home between multiple Linux installations. Not all of these are important on all installations, of course, but many systems can benefit from at least one or two of them.

[quote=spiky001]It has bt4 on as sdb system takes quite a bit so I split it this way.[/quote]

Sorry, I can't parse this.

[quote=spiky001]As  normally it is run as root so I decided to add a user leaning to safety  side and yes if I find it wrong I can change it 	[/quote]

What is "it"? The Linux OS as a whole runs components as many different users, mostly root and server-specific accounts. As a general rule, *you* as a login user should *not* run as root; that's a very dangerous practice, and if you do this, sooner or later you'll make a mistake that will be very damaging, like accidentally deleting half the system's files. You should use a conventional user account and use root (typically via the sudo command in Ubuntu) only when it's absolutely necessary.

---

### Post by spiky001 on 2010-10-02
> 
What is "it"? The Linux OS as a whole runs components as many different users, mostly root and server-specific accounts. As a general rule, *you* as a login user should *not* run as root; that's a very dangerous practice, and if you do this, sooner or later you'll make a mistake that will be very damaging, like accidentally deleting half the system's files. You should use a conventional user account and use root (typically via the sudo command in Ubuntu) only when it's absolutely necessary.

Yes I know but back track runs as root I set up a login user so as not to be root it,s just how it,s made.

---

### Post by psusi on 2010-10-02
> **srs5694 said:**
> That only works if you're re-installing or upgrading the same OS version and if the original installation is in working condition. With a separate /home partition, you can switch to a different distribution entirely, downgrade to an earlier version, or wipe the root (/) filesystem and re-install if the main installation has become hopelessly corrupted. Furthermore, my experience with in-place upgrades is mixed; they often work, but they also often create problems -- some packages may not work correctly or the whole thing sometimes refuses to boot. Thus, I often prefer to wipe the disk and re-install, or install a new distribution version side-by-side with the old one for a test period, rather than upgrade directly.

No, it works fine installing any version.  When you tell the installer not to format, it just deletes everything in /bin, /etc, etc and leaves things like /home alone.

---

