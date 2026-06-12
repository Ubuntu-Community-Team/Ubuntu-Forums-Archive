---
title: "Profiles in Users and Groups"
date: 2009-07-03
forum: General Help
---

### Post by henrywm on 2009-07-03
My Users and Groups dialog box gives three profile options: administrator, desktop user, and unprivileged.

What are the major differences between them?

---

### Post by blueridgedog on 2009-07-03
Administrators are placed in the admin group, which allows them to use sudo.  I do not know the distinction between the other two.

---

### Post by geirha on 2009-07-03
The difference is only the groups they get added to. Unpriviledged user doesn't get added to any system groups, a typical case where you'd want to create such a user would be if you only want the user to be able to upload/download some files via samba or ssh. Desktop users get added to the standard system groups you need to use the desktop, like the audio group to be able to play sounds, and the plugdev group to use pluggable devices etc. Administrator user is equal to the desktop user, but also gets added to the admin group which allows it to use sudo.

---

