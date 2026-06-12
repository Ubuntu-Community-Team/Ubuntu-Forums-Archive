---
title: "Wierd Apache+VirtualHost log permission problem"
date: 2011-10-12
forum: General Help
---

### Post by bishop__ on 2011-10-12
Hello all, 

I have configured my Ubuntu11.04 with apache and virtual host. I placed my virtual host in my local directory. 
If I start apache2 manually like this:

```
$ sudo service apache2 start 
```

Apache service will start smoothly and I can access my virtual site. 
BUT, if I reboot my machine, I notice that apache cannot start automatically. I check the logs and it has the following problem:

```

No such file or directory: apache2: could not open error log file /home/bishop/www/myapp.example.com/logs/error.log.
Unable to open logs

```

Here are the permissions of the directory path for error.log:

```

$ ls -al | grep home
drwxr-x--x   4 root     root      4096 2011-07-26 13:51 home

$ ls -al | grep bishop
drwxr-x--- 60 bishop bishop 16384 2011-10-13 08:05 bishop

$ ls -al | grep www
drwxr-xr-x  3 bishop www-data   4096 2011-09-29 16:07 public_html
lrwxrwxrwx  1 bishop bishop       12 2011-08-31 16:27 www -> public_html/

$ ls -al | grep myapp.example.com
drwxr-xr-x  6 bishop www-data  4096 2011-10-10 21:02 myapp.example.com

$ ls -al | grep logs
drwxrw----  2 bishop www-data 4096 2011-09-13 10:29 logs

$ ls -al | grep error.log 
-rwxrw---- 1 bishop www-data  198830 2011-10-12 10:15 error.log

```

---

### Post by bishop__ on 2011-10-13
help me if you can i'm feeling down. :)

---

