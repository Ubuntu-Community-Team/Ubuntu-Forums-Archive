---
title: "change name of home folder"
date: 2012-02-05
forum: General Help
---

### Post by 123456789123456789123456 on 2012-02-05
This may seem as a dumb question, I think what I have planned will work, I just need to know for sure.

When I was working on someones computer, doing an upgrade install, I misspelled the persons name, so the login user name and the home folder had the incorrect name, but since it was an upgrade install, the old home folder with the correct name still exists.

I should be able to rename the old/original home folder, then log in as root on the system, and rename the current, incorrect named home folder, to represent the correct name, and that should not cause any problems with the operation of the system

Am I correct in this?

---

### Post by pqwoerituytrueiwoq on 2012-02-05
[FONT=Courier New]usermod -l **newname** -m -d /home/**newname oldname**[/FONT]

run that as root, that should do it (may have to do that from recovery mode)


renaming the folder does not change the user name

---

### Post by 123456789123456789123456 on 2012-02-05
> **pqwoerituytrueiwoq said:**
> [FONT=Courier New]usermod -l **newname** -m -d /home/**newname oldname**[/FONT]

run that as root, that should do it (may have to do that from recovery mode)


renaming the folder does not change the user name

what if I already went ahead and changed the username through the gui?
I guess this will work also.  Thanks, I will try this.

---

### Post by 123456789123456789123456 on 2012-02-05
well that command did not work, since I already used user accounts, to change the user name eariler, it told me the user already exists, would not let me change.  I used root to rename the home folder, however when I logged back in as the user, no network connection.

if after restart of the computer, still no network connection, I may have to try another upgrade installation to fix that.

---

### Post by 123456789123456789123456 on 2012-02-05
This thread is now solved.

Explanation of everything I did

The correct user was originally on the system, display issues forced me to do an upgrade install, when I did this, I entered in the user name incorrectly, since the user originally existed on the computer, the installer simply left it there, and created the incorrect user name.
-when I found out the correct spelling of the name I corrected the user name by changing it in user accounts pannel.  This of course did not change the home folder.  When I tried to do the command suggested, it told me the user already existed.
-I used root to rename the original home folder, and then to rename the incorrectly named user folder.
-for some reason after logging back in, it lost network connection, but after restart of the computer, network connection was fine.

changing the status to solved, thanks for the suggestion.  I am sure if I did not already change the user name, that would have worked perfectly fine.

---

