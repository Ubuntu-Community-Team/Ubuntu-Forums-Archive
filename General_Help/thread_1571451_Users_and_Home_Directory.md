---
title: "Users and Home Directory"
date: 2010-09-09
forum: General Help
---

### Post by Lifespent on 2010-09-09
I am trying to setup an FTP client on Ubuntu 10.04 LTS so that when a user logs in he is directed to '/var/www' however when I go to:

System > Administration > User & Groups

I select the user account which I want to edit, I go to "advanced settings". I enter my password to authenticate. I then change the home directory from '/home/user' to '/var/www' I then click OK. It acts like it works but when I close out of the user setting window and reopen it the old home directory is back. 

Any ideas?

---

### Post by ubulal on 2010-09-09
That graphical tool may check if the user is the owner of the directory and/or if it's any other users home dir (apache).  Better use your FTP servers configuration to jail a user into a non-standard home dir.

---

### Post by Lifespent on 2010-09-09
Ah, I figured it out. I had to manually change:

> user: x:1001:1001:user,,,,:/home/user:/bin/false

to

> user: x:1001:1001:user,,,,:/var/www:/bin/false

in /etc/passwd.

---

