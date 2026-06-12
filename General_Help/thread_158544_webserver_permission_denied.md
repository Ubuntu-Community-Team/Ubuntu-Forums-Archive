---
title: "webserver permission denied"
date: 2006-04-11
forum: General Help
---

### Post by MaZZly on 2006-04-11
hi
im using apache2 and here is the problem:
i cant get my index.htm showing,
if i connect(from my xp machine) to 192.168.0.1 i see the content of the /var/www/ folder, but when i click for example index.html it says:
** Forbidden**
You don't have permission to access /index.html on this server.

i can only go into the apache2-default folder where i see an apache2 page

its the same if i connect [http://localhost](http://localhost) from my ubuntu machine

*edit*
i tried deleting all files in the apache2-default folder and putted my index.html there, and when i clicked the apache2-default i got:
**Forbidden**
You don't have permission to access /apache2-default/index.html on this server.

---

### Post by plumcreek on 2006-04-11
Do an 'ls -al /var/www' from the terminal and see if everyone has read permissions on the files.

---

### Post by MaZZly on 2006-04-11
im not sure how to read of that tables, but on the files i cant acces it stands "mazzly mazzly"
and on the files i can acces it stands "mazzly root"

dont really know what all the drwx and stuff is

```

totalt 9360
drwxr-xr-x   6 mazzly root      4096 2006-04-11 02:00 .
drwxr-xr-x  15 root   root      4096 2006-04-10 21:48 ..
-rwx------   1 mazzly mazzly     118 2006-02-16 22:09 active.asp
drwxr-xr-x   2 mazzly root      4096 2006-04-11 02:08 apache2-default
-rwx------   1 mazzly mazzly     164 2006-02-15 23:04 bg.css
drwx------   2 mazzly mazzly    4096 2006-04-11 00:41 bilder
-rwx------   1 mazzly mazzly     389 2003-02-06 01:00 global.asa
-rwx------   1 mazzly mazzly     903 2006-02-15 23:17 main.htm
drwx------   2 mazzly mazzly    4096 2006-04-11 01:06 Ny mapp
-rwx------   1 mazzly mazzly 2736626 2006-03-21 19:40 test.3gp
drwx------   2 mazzly mazzly    4096 2006-04-11 02:00 website


```

---

### Post by cskeide on 2006-04-11
I'll use two of the files as examples in order to explain the problem.
```

drwxr-xr-x   2 mazzly root      4096 2006-04-11 02:08 apache2-default
-rwx------   1 mazzly mazzly     164 2006-02-15 23:04 bg.css

```
Now, apache2-default has the following set of permissions: drwxr-xr-x. This means that the owner of the file (mazzly) has read, write and execute permissions, while the group (root) and all other users has read and execute permissions only.

The file bg.css, however, is only readable by the file's owner. In order to correct this for all files in that directory and subdirectories, issue the following in the terminal:
```
cd /var/www
sudo chmod -R +rx *
```

By the way, you wouldn't by any chance be Norwegian, would you? =)

---

### Post by plumcreek on 2006-04-11
[quote=MaZZly]im not sure how to read of that tables, but on the files i cant acces it stands "mazzly mazzly"
and on the files i can acces it stands "mazzly root"

dont really know what all the drwx and stuff is[/quote] 
Here's an example:

```
$ ls -al /var/www
total 228
drwxr-xr-x  18 plumcreek plumcreek  4096 2006-03-14 09:47 .
drwxr-xr-x  16 root      root       4096 2006-02-22 05:09 ..
-rw-r--r--   1 plumcreek plumcreek    732 2005-01-12 02:27 index.html
-rw-r-----   1 otheruser otheruser   732 2005-01-12 02:27 index2.html

``` 
In the above example, /var/www (represented by the line ending in a .) is owned by me, it is a directory (d), I have read (r) write (w) and execute (x) permissions, the group has read and execute permissions, but not write (-), and everyone else has read and execute permissions.

The file 'index.html' is owned by me, I have read and write permisions, and the group and everyone else both have read-only permissions.

The file 'index2.html' is owned by otheruser, he has read and write permissions, anyone in the 'otheruser' group has read-only permissions, but no-one else can read or do anything to the file (except root, but that's another story).

What you want to do is make sure that everyone has at least read permissions on the files in /var/www. Use this command to do that:

```
sudo chmod -R 755 /var/www
``` 
The above will ask you for your password and then give every file in /var/www read and execute permissions. That should fix any permissions errors.

---

### Post by MaZZly on 2006-04-11
thank u, that did the job!

now i got another problem, my site which contains the letters åäö bugs, it just shows a &#65533; instead of åäö.

Question 2:
when i try to connect the homesite using my ip xxx.xxx.xxx.xxx("internet ip", not local) it just shows a blank page, are there any ports i need to open?

---

### Post by raimo on 2006-04-11
1. Fast way is set Apache defaut charset to UTF-8
Add to:
/etc/apache2/apache2.conf
or
/etc/apache2/httpd.conf
line: **AddDefaultCharset UTF-8**
now those nice åöä marks will be showed right in all Your documents,
but if You use Perl or PHP etc. You must send header as UTF-8 to get
those marks showed right, here is Perl header example:
print "Content-type: text/html; charset=UTF-8\n\n";

2. port 80 must be opened

---

### Post by MaZZly on 2006-04-11
doesnt seem to work setting AddDefaultCharset utf-8, tried adding it to both files and none of em worked, i also restarted apache2

opening port 80 didnt help (i think it was open already, but i opened it to be sure)

*edit* got the åäö working, by changing the html coding to "Unicode (UTF-8 )"

---

### Post by raimo on 2006-04-11
Check is port 80 really open: [http://www.whatsmyip.org/ports/](http://www.whatsmyip.org/ports/)

---

### Post by MaZZly on 2006-04-11
port 80 = open

---

### Post by pany on 2006-07-19
In order to get åäö running you should use THIS:
AddDefaultCharset       ISO-8859-1
Put it in apache2.conf or httpd.conf.

Works for me. :)

/P

---

### Post by gomisute on 2008-02-07
If you want to access your server from outside of your network, you have to tell your router to FORWARD port 80 to your server's LOCAL IP!
And of course, you will need to have port 80 open as well (if that is your port for apache)...by default that is the port...but it can be changed through the apache config file.

---

