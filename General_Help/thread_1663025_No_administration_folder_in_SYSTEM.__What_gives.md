---
title: "No administration folder in SYSTEM.  What gives?"
date: 2011-01-09
forum: General Help
---

### Post by Smipims on 2011-01-09
I'm trying to follow the directions [here]("http://ubuntuforums.org/showthread.php?t=1604868").  However, I don't have an "administration" folder.  I only see Boot and System Volume Information and bootmgr.  Where is the folder?  Did I install something wrong?  I didn't get this problem on my other laptop.

---

### Post by coffeecat on 2011-01-09
System > Administration refers to the main menu at the top of the gnome desktop, not system folders. Are you using Ubuntu/gnome and not Kubuntu or one of the other Ubuntu-derived variants?

Your mention of a System Volume Information folder suggests a NTFS filesystem. Are you using a Wubi installation, that is Ubuntu installed inside Windows?

---

### Post by Quackers on 2011-01-09
Welcome to UF.
I believe System > Admin in this case means the headings on the Ubuntu desktop. You appear to be looking inside Windows.

---

### Post by Smipims on 2011-01-09
> **coffeecat said:**
> System > Administration refers to the main menu at the top of the gnome desktop, not system folders. Are you using Ubuntu/gnome and not Kubuntu or one of the other Ubuntu-derived variants?

Your mention of a System Volume Information folder suggests a NTFS filesystem. Are you using a Wubi installation, that is Ubuntu installed inside Windows?

Yes, it's ubuntu inside of windows.  If I do a separate partition, would that solve the problem?  If the answer to that is yes, how do I uninstall my current ubuntu installation?

---

### Post by coffeecat on 2011-01-09
You haven't told us what the problem is. :wink: If it's just trying to get your Broadcom card working, then have a look here:

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

---

### Post by Smipims on 2011-01-09
> **coffeecat said:**
> You haven't told us what the problem is. :wink: If it's just trying to get your Broadcom card working, then have a look here:

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

I believe I did accurately state my problem.

---

### Post by coffeecat on 2011-01-09
> **coffeecat said:**
> You haven't told us what the problem is. :wink:

> **Smipims said:**
> I believe I did accurately state my problem.

I was referring to this:

> **Smipims said:**
> If I do a separate partition, would that solve the problem?

Whether or not you have a Wubi install or Ubuntu on its own partition makes no difference to whether you can use the System > Administration menu. Wubi is not a problem in itself, just another way of installing Ubuntu. Quackers and I have answered your original question; do you have any others?

By the way, if you are using Wubi, beware of updates. Before you do any updates, have a look at the OP of this thread:

[http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)

And do you need help with your Broadcom wireless card?

---

### Post by Smipims on 2011-01-09
> **coffeecat said:**
> I was referring to this:



Whether or not you have a Wubi install or Ubuntu on its own partition makes no difference to whether you can use the System > Administration menu. Wubi is not a problem in itself, just another way of installing Ubuntu. Quackers and I have answered your original question; do you have any others?

By the way, if you are using Wubi, beware of updates. Before you do any updates, have a look at the OP of this thread:

[http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)

And do you need help with your Broadcom wireless card?
Well I followed the steps you listed in your first link to no avail (once I figured out the administrator stuff).  It says "searching for drivers" and then comes up with nothing.

---

