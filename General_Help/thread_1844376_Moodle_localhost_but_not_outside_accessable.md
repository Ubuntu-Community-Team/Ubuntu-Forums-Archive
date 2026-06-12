---
title: "Moodle localhost but not outside accessable"
date: 2011-09-15
forum: General Help
---

### Post by ELMIT on 2011-09-15
I am blind, ... can anybody enlighten me.

I have setup moodle and used it with [http://localhost/moodle](http://localhost/moodle)
and it works great.

I have a dynamic dns to connect from outside to that server, but I cannot access it.

apache.conf
> Alias /moodle /usr/share/moodle/

<DirectoryMatch /usr/share/moodle/>


apache.vhost.conf
> <VirtualHost *:80>
        ServerAdmin webmaster@localhost
	ServerName localhost
        DocumentRoot /usr/share/moodle/
        <Directory /usr/share/moodle/>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride None
                Order allow,deny
                allow from all

should be enough, but it isn't. What do I miss?

[http://localhost/moodle](http://localhost/moodle)   works
[http://myhost.gotdns.org/moodle](http://myhost.gotdns.org/moodle)   does not work

---

### Post by ELMIT on 2011-09-15
Solved:

> You need to read /usr/share/doc/moodle/README.Debian

It will tell you to comment a line in /etc/moodle/apache.conf

manuel.

---

### Post by dcstar on 2011-09-15
> **ELMIT said:**
> Solved:

Please read my sig.

---

### Post by ELMIT on 2011-09-15
David, you have a very nice signature, ....

Did you see mine?

---

### Post by dcstar on 2011-09-15
> **ELMIT said:**
> David, you have a very nice signature, ....

Did you see mine?

Did you even **bother** to read how to mark this thread as Solved so those of us who try to help people like you don't waste our time reading threads that are already solved?

---

### Post by ELMIT on 2011-09-15
Dear David,

I marked the thread as solved.

While already having your attention, do you know that we gone in the meantime to 11.04? soon to 11.10. Maybe you could upgrade to stay UPTODATE.
Or do you have any reason to stay on an old version longer?


Glad we had that sorted out. 


... and I added the [SOLVED] again, since my version of Firefox does not provide a dropdown menu to get this in automatically when I am writing a reply. 


Since you know now that it is solved, don't bother to reply. Just stop reading where you hit the first time the word [SOLVED], except you want to know what was the solution, then read ahead.

---

