---
title: "Making 1 profile default when more than 1"
date: 2011-06-23
forum: General Help
---

### Post by william_ia on 2011-06-23
We have a stripped down version of Ubuntu 10.04 with no menu options for security. On the admin profile we have set up a terminal window for editing or adding users.

We have created a second user with no admin privileges which we want to make the default on start up. This account is set to auto-login and takes them to a generic screen with just one icon to select and do anything with. I need to make this user the default on start up instead of the admin account as we do not want users knowing there is anything else available.

When using the $ :users-admin in the terminal window to build the other account I have no option to make one or the other default. Is this done from the command line or is there another way of making this happen?

---

### Post by william_ia on 2011-06-23
Found the answer with a little more research on my part.

We have another machine with full blown Ubuntu 10.04 still installed on it. Went to the menu and found that all I had to do was create a launcher icon of:

Login Screen
gdmsetup

then run that when the icon becomes active and contine from there.
Hopefully this will help someone else.

---

