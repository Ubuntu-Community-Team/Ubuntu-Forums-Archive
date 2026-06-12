---
title: "create link to /opt/lampp/htdocs?"
date: 2011-12-08
forum: General Help
---

### Post by qwertyjjj on 2011-12-08
How can I create a link on the desktop to /opt/lampp/htdocs/ ?
I tried right clicking on the folder and it does not give me the option.

---

### Post by qwertyjjj on 2011-12-09
bump

---

### Post by mikejonesey on 2011-12-09
```
cd ~/Desktop
ln -s /opt/lampp/htdocs/
```
or
```
ln -s /opt/lampp/htdocs/ ~/Desktop/
```

---

### Post by qwertyjjj on 2011-12-11
> **mikejonesey said:**
> ```
cd ~/Desktop
ln -s /opt/lampp/htdocs/
```
or
```
ln -s /opt/lampp/htdocs/ ~/Desktop/
```

The link is there now but I can't put any files in the folder, I get permission denied.

---

### Post by spiky001 on 2011-12-11
Have you tried just dragging the file onto desktop As user?

---

### Post by satanselbow on 2011-12-11
It is by no means a "secure solution" for production means but for a purely sandboxed developmental environment you can kinda flip it on your head and keep your pages in a folder under your home - symlinking it back to the apache document root.


Basic idea goes:

copy existing document root to folder under home.
remove original document root folder
create symlink to new docroot location in original location.

---

### Post by qwertyjjj on 2011-12-11
How can I sudo the normal user so that I can use the drag and drop normally without using the terminal?

---

### Post by satanselbow on 2011-12-11
If you set it up (with your docroot within your /home) you will not need to "sudo" nautilus - once you have set your environment up ;)

It was a bit of a fly-by post earlier but I can post full instructions if you want to go that way ;)

To use nautilus as "sudo":

```

gksu nautilus

```

Any additional windows you spawn with CTRL+N will also have the raised privileges.

---

### Post by qwertyjjj on 2011-12-12
> **satanselbow said:**
> If you set it up (with your docroot within your /home) you will not need to "sudo" nautilus - once you have set your environment up ;)

It was a bit of a fly-by post earlier but I can post full instructions if you want to go that way ;)

To use nautilus as "sudo":

```

gksu nautilus

```

Any additional windows you spawn with CTRL+N will also have the raised privileges.

I put the folder in Documents and chown'ed it to my username.
However, now I get this error when going to [http://localhost:](http://localhost:)
```

Access forbidden!

You don't have permission to access the requested directory. There is either no index document or the directory is read-protected.

If you think this is a server error, please contact the webmaster.
Error 403
localhost
Mon 12 Dec 2011 18:40:42 GMT
Apache/2.2.21 (Unix) DAV/2 mod_ssl/2.2.21 OpenSSL/1.0.0c PHP/5.3.8 mod_apreq2-20090110/2.7.1 mod_perl/2.0.5 Perl/v5.10.1 

```

```

~/Documents$ ls -l
total 49348
drwxr-xr-x 4 j j     4096 2011-12-12 18:32 htdocs

```

```

j@j-Inspiron-9300:~/Documents$ cd /opt/lampp/
j@j-Inspiron-9300:/opt/lampp$ ls -l
total 160
drwxr-xr-x  2 root root 12288 2011-09-19 17:34 bin
drwxr-xr-x  2 root root  4096 2004-07-14 15:04 cgi-bin
drwxr-xr-x  3 root root  4096 2009-04-13 17:38 error
drwxr-xr-x  8 root root  4096 2011-09-19 12:29 etc
lrwxrwxrwx  1 root root    28 2011-12-12 18:36 htdocs -> /home/j/Documents/htdocs
drwxr-xr-x  4 root root  4096 2011-12-12 18:35 htdocs.replaced
drwxr-xr-x  3 root root  4096 2003-05-31 00:38 icons
-rwxr-xr-x  1 root root 15325 2011-09-02 11:41 lampp
drwxr-xr-x 15 root root 12288 2011-12-08 20:46 lib
drwxr-xr-x  2 root root  4096 2006-04-26 18:46 libexec
drwxr-xr-x 36 root root  4096 2009-08-24 07:52 licenses
drwxr-xr-x  2 root root  4096 2011-12-12 18:40 logs
drwxr-xr-x  2 root root  4096 2011-09-19 17:33 modules
drwxr-xr-x 10 root root  4096 2011-12-08 20:46 phpmyadmin
-rw-rw-r--  1 root root 65212 2011-09-19 11:50 RELEASENOTES
drwxr-xr-x  2 root root  4096 2011-09-19 17:34 sbin
drwxr-xr-x 39 root root  4096 2011-09-19 17:33 share
drwxr-xr-x  3 root root  4096 2005-01-18 20:21 tmp
drwxr-xr-x  6 root root  4096 2011-12-12 18:40 var
jason@jason-Inspiron-9300:/opt/lampp$ 


```

Can I do this instead? sudo chmod 777 -R /opt/lampp/htdocs/

---

