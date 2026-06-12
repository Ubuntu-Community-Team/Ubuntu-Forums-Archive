---
title: "how to reinstall so that php.ini gets restored"
date: 2011-03-17
forum: General Help
---

### Post by Pacopag on 2011-03-17
Hi.  Can someone please tell me how I can restore my php.ini file back to the way it was when php5 was first installed on my system.  The best thing would be to "just" restore this file, but the most important thing is that mysql databases are left intact.

Thanks,

---

### Post by andrewthomas on 2011-03-18
> 
[SIZE=2]PHP comes packaged with two INI files. [/SIZE]
[SIZE=2]One that is recommended to be used in production environments [/SIZE]
[SIZE=2]and one that is recommended to be used in development environments. [/SIZE]
[SIZE=2]**php.ini-production** contains settings which hold security, performance and best practices at its core.[/SIZE]
[SIZE=2]**php.ini-development** is very similar to its production variant, except it's much more verbose when it comes to errors. We recommend using the development version only in development environments as errors shown to application users can inadvertently leak otherwise secure information.[/SIZE]

 
 
[SIZE=2]look in [/SIZE]
 
```
 
/usr/share/doc/php5-common/examples/php.ini-development
/usr/share/doc/php5-common/examples/php.ini-production
/usr/share/php5/php.ini-production
 

```

---

### Post by Pacopag on 2011-03-18
That's perfect.  Thanks.

---

### Post by andrewthomas on 2011-03-18
You're welcome.  

Glad to be of help.

---

### Post by pterosky on 2011-06-20
Thanks a bunch, it was driving me mad! Restoring my php.ini from php.ini-development fixed it for me as well.

These settings worked, after I inserted them in my brand new php.ini:

```
max_execution_time = 120
max_input_time = 90
memory_limit = 128M
post_max_size = 128M
upload_max_filesize = 128M
session.gc_maxlifetime = 14400
```

---

