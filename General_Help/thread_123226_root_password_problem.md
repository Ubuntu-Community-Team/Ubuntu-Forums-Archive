---
title: "root password problem"
date: 2006-01-29
forum: General Help
---

### Post by njmarine2001 on 2006-01-29
ok every time i try to do something from gnome and that would normally require root access i get asked for the root pass. yes i know this is supposed to happen like that and its good

the problem comes in that i enter the root password and it says wrong password and gives me the close dialog

sudo passwd root says sorry try again and after three attempts with the correct password it says 3 attempts failed

i know the password is correct cause i can su root and get root access that way.

any solution to make gnome see the correct password when i enter it?

---

### Post by kaamos on 2006-01-29
sudo (and so all the "root" options in gnome menus) is asking for your **user** password, not root

---

### Post by njmarine2001 on 2006-01-29
If i put in the user pass it says unable to run as root wrong password

---

### Post by njmarine2001 on 2006-01-29
problem solved.

i ended up reinstalling, i think it all stemmed from the fact that i did not create a user during the initial installation of the program, then went back with the recovery mode and adduser for a new user and that user while able to log in couldnt actually do very much, i couldnt get much of anythin to load except forefox.

---

