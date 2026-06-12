---
title: "Deleting user fails"
date: 2009-11-03
forum: General Help
---

### Post by kumoshk on 2009-11-03
So, I've noticed that in Karmic, I can't seem to delete the user I started with (while using another user with administrative privileges). It acts like it lets me, but then I go back and the user is there again (plus it's there at login). It's even there if I delete its folder from the home directory.

How to I get rid of this user without reinstalling?

I never had this problem in previous releases (and I have tried). It's fairly common for me to do this, believe it or not (since I like to preserve *some* stuff from a previous home directory, without having to worry about conflicting settings by backing up everything, when installing a new distribution, in a fashion that requires this, unless I want to be tedious).

---

### Post by isoToxin on 2009-11-03
You can use the 'userdel' command from a terminal to get rid of the account.  I couldn't delete a user from the GUI in 9.10 either btw, but 'userdel' command worked fine.

Syntax is:

sudo userdel <username>

you can use the -r switch to remove home folder too.

---

### Post by kumoshk on 2009-11-03
Awesome! Thanks. That made my day.

I love the command-line. (It worked, just in case those who need convincing are curious.)

---

### Post by isoToxin on 2009-11-03
No problem, glad to help.  :)

---

