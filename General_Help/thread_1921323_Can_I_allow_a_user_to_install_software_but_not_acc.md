---
title: "Can I allow a user to install software but not access Network Manager?"
date: 2012-02-06
forum: General Help
---

### Post by link470 on 2012-02-06
Hello!  I'd like to distribute a couple of sample laptops to certain individuals to use the Ubuntu Software Center so they can discover and try out Linux software.  I was previously looking for a way to disable the Network Manager or mask/encrypt the wireless password permanently.  This doesn't seem to be doable.  So I've resorted to using two user accounts.

What I'm trying to do is have one admin user account that can access the full system [including Network Manager to set the connection], and then another user that has the ability to install software, but NOT configure network connections via the Network Manager.  Is this possible?  I tried changing the software install user's privileges by unchecking "connect to wireless and ethernet networks", but that seems to do absolutely nothing as long as "administer the system" is also checked.  The only difference I see now when I go up to network manager is that the system asks for authentication, but I can authenticate with either of the two users and get in perfectly fine.

Is there any combination of settings/permissions/user accounts that will allow me to configure a wireless network connection with one account, and then have another account that can install software and not touch network connections?  I'd still like them to be able to use wireless obviously, just not read/edit the settings.  I realize that a skilled user could most likely bypass whatever measures I put in place to do this, but I'd just like a simple solution to prevent the average user from going exploring.

Thanks!

---

### Post by ajgreeny on 2012-02-06
Have a look at [https://help.ubuntu.com/community/Sudoers](https://help.ubuntu.com/community/Sudoers) which may help.

Proceed with caution!  It could be dangerous.

---

