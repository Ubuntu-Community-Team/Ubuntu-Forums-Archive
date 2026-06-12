---
title: "FTP work fine but no upload to linked dir"
date: 2012-06-09
forum: General Help
---

### Post by Andre72 on 2012-06-09
Hi,

I installed vsftpd some days ago and can't make it work as required.
Whan a user connect he can upload to the home directory.
But I create a link from this home directory to a www directory for the user.
Owner and group of the www directory is www-data:www-data

The user is also member of www-data:
useradd -g www-data theuser

Group rights seems ok (I think):[FONT=monospace]
[/FONT]drwxrwxr-x  8 www-data     www-data     4096 2011-04-23 00:41 www

But upload or create a dir is denied inside www ...

Is there something more to do?
What is the reason for is this a vsftpd or user rights issue?

I'm using ubuntu 10.4
Can you help me please to make it work ...?

Thanks

Andre

---

### Post by codemaniac on 2012-06-09
Have you tried changing the ownership of the folder and add the user "theuser" to own it ?
```
chwon -R theuser:www-data /var/www
chmod 775 /var/www
```

---

### Post by Andre72 on 2012-06-09
Thanks it works fine now.
I thought to be rember of the group would be enogh ...

---

### Post by codemaniac on 2012-06-09
Please mark this thread as solved , so that others people can reuse it .

---

