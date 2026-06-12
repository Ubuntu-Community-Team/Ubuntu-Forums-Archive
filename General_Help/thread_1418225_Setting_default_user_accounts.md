---
title: "Setting default user accounts"
date: 2010-02-28
forum: General Help
---

### Post by mooserider2 on 2010-02-28
I'm using ubuntu and i need to know if it is possible to make a "prototype" account that sets the defaults for new users when a new account is made. How would i go about doing this. I would like to have the same start up programs, panel, themes, background, etc...

---

### Post by cjhabs on 2010-02-28
> **mooserider2 said:**
> I'm using ubuntu and i need to know if it is possible to make a "prototype" account that sets the defaults for new users when a new account is made. How would i go about doing this. I would like to have the same start up programs, panel, themes, background, etc...

useradd uses the files in /etc/skel as the defaults from which the new user account is created.

---

### Post by mooserider2 on 2010-02-28
In my /ect/skel i have a thing called examples and when I open it it brings me to /user/share/example-content. In this file there is a logo file with ubuntu and the variants logos, some jpgs, odts, odps, an audio book, and a xls. I'm not quite sure what that means. If someone could elaborate.

---

### Post by cjhabs on 2010-02-28
There are hidden files in there also, such as .bashrc.
Everything that you place in /etc/skel gets copied to the new user's home directory, including the examples.desktop file, so set up /etc/skel with all the files you would like in the new users home folder and create the account.

---

### Post by mooserider2 on 2010-02-28
how would i set the background panel theme and startup programs. Could i just copy the .bashrc, from my current user into /ect/skel

---

### Post by mooserider2 on 2010-02-28
Oh wait I got it copy all the hidden files. Sweet it works thanks guys this really helped:P

---

### Post by cjhabs on 2010-02-28
Please mark this as resolved in the thread tools.

Glad it worked!

---

