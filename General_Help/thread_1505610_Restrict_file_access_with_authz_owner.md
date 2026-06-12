---
title: "Restrict file access with authz_owner"
date: 2010-06-09
forum: General Help
---

### Post by Bob1987 on 2010-06-09
Hi everyone,

I'm running a Virtual Box with Ubuntu 9.10 and I'm experimenting with Apache 2.2.12

I would like to use the authz_owner module but it is not possible for me to access [http://localhost/~b/private/]("http://localhost/%7Eb/private/")

"b" is my username and "private" is the directory definded in the httpd.conf file.

My httpd.conf file:
```
<Directory /home/*/public_html/private>
    AuthType Basic
    AuthName "insert password"
    AuthBasicProvider dbm
    AuthDBMUserFile /etc/apache2/etc/htmdb
    Satisfy All
    Require file-owner
</Directory>

```The AuthDBMUserFile contains the User "b" too and /home/*/public_html/private is owned by "b".

I'm able to access [http://localhost/](http://localhost/) and [http://localhost/~b/]("http://localhost/%7Eb/") without any problems.

---

### Post by dino99 on 2010-06-09
[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

---

### Post by Bob1987 on 2010-06-10
Thank you for the Link.

Furthermore i read the error.log 
> [Thu Jun 10 03:43:08 2010] [error] [client 127.0.0.1] (2)No such file or directory: Authorization of user b to access /~b/private/index.htm failed, reason: could not stat file /home/b/public_html/private/index.htmI created an index.htm file into the protected folder and I was able to access it.
Why do I need the index file? I thought > If you direct your web browser to a directory (rather than a specific  file), and there is no  "index.html" file in that directory, Apache  will generate an index file on-the-fly listing all the files and  folders in that directory.

---

