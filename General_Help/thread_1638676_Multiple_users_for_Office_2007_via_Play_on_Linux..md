---
title: "Multiple users for Office 2007 via Play on Linux."
date: 2010-12-05
forum: General Help
---

### Post by drcdebaca on 2010-12-05
I recently used a Make Use Of article to install Office 2007 on my kids computer for school.  The install was a success; However, the install only works for my user.  Play on linux is installed for all users, but Office 2007 only shows up for my user.  It has been suggested to me that I change the permissions for the /home/user/.Playonlinux file and the create a symlink to that file for other users.  Does that sound like it would work?  If so how would I do the symlink?

---

### Post by dcstar on 2010-12-06
> **drcdebaca said:**
> I recently used a Make Use Of article to install Office 2007 on my kids computer for school.  The install was a success; However, the install only works for my user.  Play on linux is installed for all users, but Office 2007 only shows up for my user.  It has been suggested to me that I change the permissions for the /home/user/.Playonlinux file and the create a symlink to that file for other users.  Does that sound like it would work?  If so how would I do the symlink?

[PlayonLinux]("http://www.playonlinux.com/") is based on Wine, and has all the same issues of being installed in the /home folder of a single user which means permissions etc have to be solved for other users to possibly use it.

See if there is information on using Wine programs this way and they may apply to this as well.

---

