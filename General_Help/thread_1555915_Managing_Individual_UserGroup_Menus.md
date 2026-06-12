---
title: "Managing Individual User/Group Menus"
date: 2010-08-18
forum: General Help
---

### Post by joshdale on 2010-08-18
I've been googling and searching the forums looking for this answer, and I've come up short...is there a way to manage individual user/group panel menus under an LTSP enviroment?

Basically I want to change any existing/new users that are not "admin" and dumbify their respective panel menus.  Is this achieved through the chroot LTSP installation?

Thanks.

---

### Post by joshdale on 2010-08-19
bump

---

### Post by joshdale on 2010-08-19
Upon further investigation, I found that the /etc/skel directory allows for standardization of user files when created.

Basically, I created a new user, configured what I wanted to be the standard for new users going further, and dumped all that created user's home directory files into /etc/skel.

Check out the details here: [http://www.linfo.org/etc_skel.html](http://www.linfo.org/etc_skel.html)

---

### Post by fairplay89 on 2011-02-14
> **joshdale said:**
> Upon further investigation, I found that the /etc/skel directory allows for standardization of user files when created.
 
Basically, I created a new user, configured what I wanted to be the standard for new users going further, and dumped all that created user's home directory files into /etc/skel.
 
Check out the details here: [http://www.linfo.org/etc_skel.html](http://www.linfo.org/etc_skel.html)
 
 
Thank you. This really helped me out! Not many people on these forums are familiar with LTSP so your post really helped me. :D

---

