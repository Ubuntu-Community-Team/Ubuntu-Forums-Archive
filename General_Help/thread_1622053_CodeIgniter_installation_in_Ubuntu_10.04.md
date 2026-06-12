---
title: "CodeIgniter installation in Ubuntu 10.04"
date: 2010-11-15
forum: General Help
---

### Post by kingdm on 2010-11-15
Hi there.

I am having trouble in installing CodeIgniter in my Ubuntu 10.04. I extracted the CodeIgniter-1.7.2.zip that I downloaded in their site to /var/www/training/codeigniter and it contains the following:

*index.php
*license.txt
*system (directory)
*user_guider (directory)

Now I try to run this on my browser url : 127.0.0.1/training/codeigniter, I assume that index.php will have to display but I simply get a blank screen. My LAMP is working fine, its just that it won’t display anything under the codeigniter directory.

Any ideas, why?

Regards,

Dee

---

### Post by Verbeck on 2010-11-15
check the permission of the files and see whether its readable by the 'others' group

---

### Post by kingdm on 2010-11-15
> **Verbeck said:**
> check the permission of the files and see whether its readable by the 'others' group

Thanks for your quick reply Verbeck.

I checked the permission of index.php and here is what I've got:

Owner : 777 - user #777
Access : Read and write

Group : myusername
Access : Read and write

Others : <empty>
Access : Read and write

Can you assist me in this?

Thanks.

---

### Post by Verbeck on 2010-11-15
that looks ok... try the codeigniter/system/application/config/config.php

edit : check whether changing the permissions of every file fixes it. if not, it could be just a bad download

from a terminal:
```
sudo chmod -R 775 /var/www/training/codeigniter
```

---

### Post by kingdm on 2010-11-15
I can't access the codeigniter/system directory, I get a permission denied warning.

I checked the permission, it's the same as that in index.php.

---

### Post by kingdm on 2010-11-15
Never mind my earlier reply, I've accessed the codeigniter/system/application/config/config.php and here what I got:

**-rwxrwxrwx 1 777 myusername  12K 2009-02-04 14:44 config.php**..

---

### Post by kingdm on 2010-11-15
> **Verbeck said:**
> that looks ok... try the codeigniter/system/application/config/config.php

edit : check whether changing the permissions of every file fixes it. if not, it could be just a bad download

from a terminal:
```
sudo chmod -R 775 /var/www/training/codeigniter
```

That solves my problem, cheers to you man.

Thanks a lot. :)

---

### Post by Verbeck on 2010-11-15
you're welcome

---

