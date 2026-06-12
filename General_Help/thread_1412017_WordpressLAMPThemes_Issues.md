---
title: "Wordpress/LAMP/Themes Issues"
date: 2010-02-20
forum: General Help
---

### Post by poison.designs on 2010-02-20
I've finally managed to get a local install of WP up and running but, for some reason, when I copy new theme directories into the themes folder, WP-Admin doesn't see them.

I've spent about 4 hours working my way through this and this is the last problem I've got to deal with - please help! :D

---

### Post by quixote on 2010-02-22
Weird.  The only thing I can think of is to check the permissions.  The directories all need 755 (drwxr-x-r-x) and the files need to be readable by all, ie 644 (rw-r--r--).  The webuser (which is what wordpress is) uses the permissions of the last triplet.  So, for instance, a file with permissions 640 (rw-r-----) wouldn't be readable by wordpress.

You're putting them in wp-content/themes/ right?

---

### Post by poison.designs on 2010-02-22
There it is! I was working as root for some reason. Heh. Thank you, my new hero!

---

### Post by quixote on 2010-02-22
Great!  Good to know.  (As the original poster, you can mark the thread "solved" which helps the next person. :) )  (It's up there under the "Thread Tools" dropdown.)

---

