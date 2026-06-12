---
title: "Upgrade to 10.04 messes up my encrypted home"
date: 2010-11-07
forum: General Help
---

### Post by cbhargava on 2010-11-07
Hi All,

Apparently after an upgrade, I lost access to my encrypted home directory. Looks like upgrade scripts changed the scripts that mounted my encrypted home directory.

As I don't have my ecryptfs password handy, is there any way to revert the things back as they were?

I have liked Ubuntu all the way but after this upgrade-mess-up, I might change my view.

Thanks in advance for any pointers.

---

### Post by iponeverything on 2010-11-08
> **cbhargava said:**
> Hi All,

Apparently after an upgrade, I lost access to my encrypted home directory. Looks like upgrade scripts changed the scripts that mounted my encrypted home directory.

As I don't have my ecryptfs password handy, is there any way to revert the things back as they were?

I have liked Ubuntu all the way but after this upgrade-mess-up, I might change my view.

Thanks in advance for any pointers.

There is no revert for upgrades.  From a technical perspective, it is a very complex problem. 

It would have been advisable to backup your mounted home before doing the upgrade - 20/20 hindsight. 

As for changing your view, it could be fickle or wise -- depending..

---

### Post by cbhargava on 2010-11-08
> **iponeverything said:**
> It would have been advisable to backup your mounted home before doing the upgrade - 20/20 hindsight. 

Very understandable, it was all my fault that I did not back up my home before the upgrade. I was pretty confident that nothing bad would happen with the upgrade procedure! I pretty much trusted the installer and failed.



> **iponeverything said:**
> As for changing your view, it could be fickle or wise -- depending..

Very true! Your replay clearly indicates that you are a true Ubuntu follower. I don't blame you.

---

### Post by cbhargava on 2010-11-09
It seems that the data is intact just not getting mounted automatically after the upgrade. I was able to mount the private directory by using the passphrase.

---

