---
title: "adduser or useradd ? System &gt; Administration &gt; Users and Groups"
date: 2010-08-10
forum: General Help
---

### Post by iMisspell on 2010-08-10
When a new user is created (weather it be adduser or useradd or System > Administration > Users and Groups ) i would like to automaticly add them to the www-data group.
What method does *System > Administration > Users and Groups* use ?

Just tried to edit the /etc/adduser.conf file:
EXTRA_GROUPS="dialout cdrom floppy audio video plugdev users www-data"
and tried both
ADD_EXTRA_GROUPS=1
ADD_EXTRA_GROUPS=0

But the user is not added to the 'www-data' group when using *System > Administration > Users and Groups*.

Note: I would like for this to happen automaticly during the creation of the new user with no extra steps.

Thanks for any direction.

------------------------------------------------------------------------

The over all plan of what im doing is (in case your board and want to offer some insight :) )...
Creating my own Ubuntu install with _[Remastersys]("http://www.geekconnection.org/remastersys/")_.
Did a fresh install of the GUI-less sever (in a vbox), then installed '*-no-install-recommends ubuntu-desktop*' and started to install the apps i want.
In the mist of creating the 'skel' dir now. There is a standard layout which i would like all new users to start with, Desktop icons, firefox bookmarks, menu layout, panels, etc., so Ive created one user and placed the config folder(s) which im discovering (.config, .gconf, .mozilla, .local, parts of .gnome2 is where im at now) to be necessary to achieve this in the 'skel' dir and then creating links to the current user so changes im making now - to the current user account, will create the base of new users accounts (hope that made sence).

I would like to keep '/var/www' centrally located and also have any/all users able to edit and work with files there. So this is where adding new users to the 'www-data' group come in.



_

---

### Post by sisco311 on 2010-08-11
> **iMisspell said:**
> 
What method does *System > Administration > Users and Groups* use ?


You have to edit the /etc/gnome-system-tools/user-profiles.conf file.

---

### Post by iMisspell on 2010-08-20
Just checked out the file, looks to be what im looking for, gonna test it out tomorrow.

Thanks so much, sisco311.

_

---

