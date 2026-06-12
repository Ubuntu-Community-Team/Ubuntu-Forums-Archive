---
title: "deleted .ICEauthority file"
date: 2010-11-08
forum: General Help
---

### Post by candinux on 2010-11-08
Hi,
Yesterday I changed the log-in settings.. from ask password while log-in to dont ask password.
the next time i re-boot my system got this error

error1. could not update ICEauthority file /home/user/.ICEauthority
 
after closing that pop up I got next error pop-up

error2: There is a  problem with the configuration server. (/usr/lib/libconfg2-4/gconf-sanity-check2 exited with status 256)

error3: Nautilus could not create the following required folders: /home/user/Desktop/,/home/user/.nautilus
 
thought of searching the solutin in ubuntu-forums thread.. got some  thread.. one of which i followed and deleted the .ICEauthority file :(  :(
should not have deleted that coz I got another solution like chmod stuff for it. but pathetically theh ICEauthority is deleted.
Now what can be done?

please suggest...

---

### Post by dino99 on 2010-11-08
might be still in the trash can

or recreate it:

if your user is toto

sudo adduser toto
sudo adduser toto admin

---

### Post by candinux on 2010-11-08
I created a new user by
alt+ctrl+f2
logging in
and 
sudo adduser apple
sudo adduser apple admin

then I was able to login with this user.
but I am not accessed to the folders like music, documents, home, etc of previous user.

how can I ?
can I create a .ICEauthority file for previous user?
I also want my previous user login to retrieve

---

