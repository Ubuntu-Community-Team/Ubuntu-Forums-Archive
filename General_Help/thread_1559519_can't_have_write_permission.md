---
title: "can't have write permission"
date: 2010-08-23
forum: General Help
---

### Post by dersu on 2010-08-23
Hi,
I have my second hard drive that I want to use as storage. But I can't write into if I am not root.
the owner is root,I don't want to change it as it is not adviced.
I created a datas group by "groupadd datas"
I changed my mount point data by "chgrp datas data/"
I added my username by "usermod -G datas dersu(username)"

but when I want to write into I get:
touch: cannot touch `data/asdfasdfh': Permission denied

Thanks a lot for your help.

---

### Post by Toz on 2010-08-23
You may need to log out and back in for the new group membership to take effect. Also, ensure that the group datas has write access to that directory -> 'chmod 775 data' (or as appropriate).

What does 'ls -l data' return?

/ToZ

---

### Post by dersu on 2010-08-24
Group datas has write access.
But I did not log out. I've just checked in /etc/group and it was updated, but I'll try this this evening.
Thanks.

---

### Post by jv2112 on 2010-08-24
try 

sudo chown -R name;group /the/Mount_Point (makes you owner)

then 

sudo chmod -R 775 /the/Mount_Point (gives you access)

Hope this helps.

---

### Post by dersu on 2010-08-24
I don't believe it, I should just log out.

drwxrwxr-x 3 root datas 4096 2010-08-24 12:31 data

and I can write in it by being part of the group datas.

Thanks for your helps.

---

