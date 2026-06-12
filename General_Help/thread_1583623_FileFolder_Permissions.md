---
title: "File/Folder Permissions"
date: 2010-09-28
forum: General Help
---

### Post by cvandal on 2010-09-28
Hello,

I've created a new user called cvandal on my Ubuntu 10.04 server and would like them to have write permissions to the /var/www directory and anything created within it.

I've typed the following command:
```
addgroup cvandal root
chown -R root:root /var/www
```

When I try and create a new folder or upload a new file, I get the message permission denied.

If I type:

```
chown -R cvandal /var/www
``` it works fine.

Is there a way I can allow the root and cvandal account write permission to /var/www?

---

### Post by viperce on 2010-09-28
try this..
 
chmod -R 777 /var/www
 
you can also check out this link if it does not work
[http://www.zzee.com/solutions/chmod-help.shtml](http://www.zzee.com/solutions/chmod-help.shtml)

---

### Post by linux-hack on 2010-09-28
or try this : [https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

---

### Post by meoconvn38 on 2010-09-28
Maybe sudo chown -R cvanda /var/www

---

### Post by cvandal on 2010-09-28
Thanks guys :) 775 was what I was after.

---

