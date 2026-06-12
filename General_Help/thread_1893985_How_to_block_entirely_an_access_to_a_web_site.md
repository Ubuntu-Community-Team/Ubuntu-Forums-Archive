---
title: "How to block entirely an access to a web site?"
date: 2011-12-11
forum: General Help
---

### Post by Bruno81 on 2011-12-11
Hi.

I'd like to know how to block entirely a web site....

Her's what I've done:

From terminal.....

sudo gedit /etc/hosts

after I've write  

0.0.0.0     [www.mysite.com](www.mysite.com)

When I enter into my site I can't see it..... but into the chronology I've the entire site......

For example I've [www.mysite.com/page1](www.mysite.com/page1)

I've tried to change the hosts into

0.0.0.0   [www.mysite.com*](www.mysite.com*)

but after have put the *  I can see again the main page.....what can I do for BLOCK enirely the access to the web site?

Tnx so much for the answers!!!!!!!!!!!!!!!

Best Regards.

---

### Post by dabl on 2011-12-11
Try adding to /etc/hosts:

127.0.0.1  [www.mysite.com](www.mysite.com)

Save it and restart networking, or reboot the computer.

---

### Post by Bruno81 on 2011-12-11
Hi.

Tnx for the answer but I can still see the other pages of the site..... :(

---

### Post by dabl on 2011-12-11
Are you sure your browser has not cached some pages of the site?  Try purging the cache, then see if you can find the page.

---

### Post by oldtimer7777 on 2011-12-11
Install moblock and block whatever web site you want.  It uses a GUI instead.

You can find the PPA to install it about 1/2 the way down the checklist:

[https://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/](https://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/)

> **Bruno81 said:**
> Hi.

I'd like to know how to block entirely a web site....

Her's what I've done:

From terminal.....

sudo gedit /etc/hosts

after I've write  

0.0.0.0     [www.mysite.com]("http://www.mysite.com")

When I enter into my site I can't see it..... but into the chronology I've the entire site......

For example I've [www.mysite.com/page1]("http://www.mysite.com/page1")

I've tried to change the hosts into

0.0.0.0   [www.mysite.com*]("http://www.mysite.com*")

but after have put the *  I can see again the main page.....what can I do for BLOCK enirely the access to the web site?

Tnx so much for the answers!!!!!!!!!!!!!!!

Best Regards.

---

### Post by fdrake on 2011-12-11
also check /etc/nsswitch.conf and make sure that "files" is before the "dns" server address!
you have also the ption to blacklist the address from your router's config page (if it belongs to you!).

---------------------
If this website is accessing a service to your computer. like ftp, (since you did not specify if you are blocking the site as a "server" or as a "client") add an entry to /etc/hosts.deny (if you are usin inetd super server)
> 
ALL:.example.com

or if you are using xinetd super server edit the file: /etc/xinetd.conf

---

### Post by gennatolls on 2011-12-11
I don't know if you have access to the network router but you could do it at that level as well.

---

