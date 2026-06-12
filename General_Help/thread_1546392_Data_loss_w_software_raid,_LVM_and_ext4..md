---
title: "Data loss w/ software raid, LVM and ext4."
date: 2010-08-05
forum: General Help
---

### Post by talksnmaths on 2010-08-05
Hi,

I have setup a Ubuntu Server 10.04 box for the purpose of having an internet available source code repository for my personal projects.  For the purposes of storage, I have two data drives in a software raid mirror configuration.  The array was created using the built-in software raid chip on the motherboard.  On that array, I have an LVM physical volume with multiple logical volumes for storing apache and subversion data.  The logical volume for subversion is mounted at /var/svn and is formatted as ext4.  The subversion data is available through apache and the dav_svn module as well as viewvc.  The problem that I am having is that every time we have a power outage at home, and these have been happening frequently in the Midwest these days, my subversion repositories are reset back to revision 0.  I've considered investing in a UPS, but if the power goes out while I'm at work it is still possible for the UPS to run out of juice before I get home to gracefully power the machine down.  Fortunately, I have all my latest source code pulled down at the moment, but I can't keep going on with this issue or I'm going to get screwed.  I find it odd that all my repos survive, but just get reset as opposed to getting corrupted data.  I'm hoping that given my configuration someone can provide me with some advice as to what might be going on.

Thanks!

---

### Post by jacekk015 on 2010-08-06
NUT is your friend I think
[http://www.networkupstools.org/compat/stable.html](http://www.networkupstools.org/compat/stable.html)

There's nothing you can do with power problems. The system needs to be shut down normally.

---

### Post by talksnmaths on 2010-08-08
Ahh, cool.  I'll check this out!

---

