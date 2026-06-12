---
title: "Changed password, blank desktop"
date: 2010-01-30
forum: General Help
---

### Post by mvalenti on 2010-01-30
Ubuntu 9.04

changed password by these steps...
system\administration\users and groups\user settings... highlight the user, properties, click generate random password, type password in the box, select ok and restart...

log in with user name and new password

then error messages:
could not update iceauthority file....

then

there is a problem with the configuration server..........status 256

then

nautilus could not create the following required folders
home/mark/desktop
home/mark/.nautilus


then I get a blank desktop no icons no menus...

---

### Post by julio prada on 2010-02-21
I SOLVED my problem!!!!!!
It was exactly the same.
I noticed that there was a problem when I changed my password, so what I did is:
1. Log into another user I had created.
2. Open a terminal window (menu accesories terminal).
3. Change to the damaged user using the "su myname" command.
(now I had my prompt looking like: myname@mylaptop:$~)
4. Change my password again, because the proccess was not done correctly I dont know why.
"passwd myname"
Current Password:
New Password:
Confirm New Password:
5. Exit terminal
6. Restart pc
7. Log in as new user and...

EVERYTHING IS BACK TO NORMAL!!!!!

---

