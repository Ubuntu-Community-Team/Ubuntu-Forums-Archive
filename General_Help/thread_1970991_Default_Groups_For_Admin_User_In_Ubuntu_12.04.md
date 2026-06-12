---
title: "Default Groups For Admin User In Ubuntu 12.04?"
date: 2012-05-02
forum: General Help
---

### Post by digiPixel on 2012-05-02
On a laptop running Ubuntu 12.04 LTS I foolishly followed some instructions on adding a user to a secondary group. After executing the command (usermod) I can no longer use the **sudo** command. Should have followed my insticts after doing some reading of the man page for **usermod** where the **a** switch needs to be added before the **G** switch.

My Linux CLI knowledge is a bit rusty however I discovered via the **groups** command that my user is now only a member of 2 groups (incl the user's group). Only one user exists in the system since the OS was installed via a Net Install.

What are the default groups that an admin user is a member of in Ubuntu 12.04?

Made a mistake in creating this thread in the wrong group. This thread should be in the **General Help** group. Is there any way to move this thread?

---

### Post by aysiu on 2012-05-02
You should be in *adm cdrom sudo dip plugdev lpadmin sambashare*

---

### Post by aysiu on 2012-05-02
> **digiPixel said:**
> After executing the command (usermod) I can no longer use the **sudo** command. You can fix that:
[http://www.psychocats.net/ubuntu/fixsudo](http://www.psychocats.net/ubuntu/fixsudo)

---

### Post by digiPixel on 2012-05-02
> You should be in adm cdrom sudo dip plugdev lpadmin sambashare

> **aysiu said:**
> You can fix that:
[http://www.psychocats.net/ubuntu/fixsudo](http://www.psychocats.net/ubuntu/fixsudo)

That did the trick, thanks. Will teach me to enter in a command without checking it first.

Now i'm wondering why Canonical decided to remove group management from User Accounts. Would have made adding a user to a new group less error prone.

---

