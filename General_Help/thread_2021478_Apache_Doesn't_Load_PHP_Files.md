---
title: "Apache Doesn't Load PHP Files"
date: 2012-07-09
forum: General Help
---

### Post by theopfor on 2012-07-09
I was setting up a LAMP server for personal use yesterday, and my php files just loaded up a white page. I fiddled around in the php.ini and I got it to load text, but that text was an error.

> Warning: Unknown: failed to open stream: Permission denied in Unknown on  line 0  Fatal error: Unknown: Failed opening required '/var/www/index.php'  (include_path='.:/usr/share/php:/usr/share/pear') in Unknown on line 0 

I don't know what it means, and I don't have a /usr/share/pear folder. I did some googling and that didn't turn up anything helpful. How can I fix this?

---

### Post by spjackson on 2012-07-09
The account under which apache is running (usually www-data) does not have read access to the file /var/www/index.php. Check the file ownership and permission of index.php and /var/www.

---

### Post by theopfor on 2012-07-09
I gave the group www-data full control over /var/www/ but now I get errors from the files inside. I set all the permissions inside the folders to give full control, but now I am getting include errors of the same type.


EDIT: Never mind, I think it might be working now, thanks!

---

