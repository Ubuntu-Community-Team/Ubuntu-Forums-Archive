---
title: "How to add files to /var/www/ ?"
date: 2011-11-20
forum: General Help
---

### Post by simpie on 2011-11-20
Hallo everybody!

I am new to ubuntu, so can you please tell me how to put my files in /var/www or in the root directory?
Because I can't paste or remove files in /var/www and if that is done I can actually continue with my site.
Because it didn't worked in user directories. And my PHP5 is already enabled. 

I used EasyPHP in windows that was very simple.
I already have installed LAMP. And if I type localhost in my browser's address bar he says: It works!

Thanks...

---

### Post by Rocket2DMn on 2011-11-20
simpie, please start a new thread for your problem.  Thanks.

---

### Post by CharlesA on 2011-11-20
Hi,

You would need to move them using sudo (or gksu if you are using a GUI).

Either do that or tell apache to serve the files from a folder in your home directory - that way you don't need to have root permissions to add or change files there.

[http://www.debianadmin.com/apache2-installation-and-configuration-with-php-support-in-debian-linux.html](http://www.debianadmin.com/apache2-installation-and-configuration-with-php-support-in-debian-linux.html)

---

### Post by Lars Noodén on 2011-11-20
If you're not sharing /var/www with any other users, then you only need to worry about creating access for yourself:

```

sudo chgrp -R simpie /var/www
sudo find /var/www -type d -exec chmod g=rwxs {} \;
sudo find /var/www -type f -exec chmod g=rws  {} \; 

```

If you are sharing access among several users, then make them members of a group (e.g. 'webmasters') and substitute that group for 'simpie' above.

---

### Post by fdrake on 2011-11-20
@Lars Noodén
i think you should make sure that the files he is creating are accessible and executable for the user www-data since he is running a webserver. That said he should make sure that www-data is inside the webmaster group even if he is the only webmaster. and make all the files executable to the user and the group.

---

### Post by CharlesA on 2011-11-20
> **fdrake said:**
> @Lars Noodén
i think you should make sure that the files he is creating are accessible and executable for the user www-data since he is running a webserver. That said he should make sure that www-data is inside the webmaster group even if he is the only webmaster. and make all the files executable to the user and the group.
www-data should only have read access.

In my case, I changed the document root to point to a folder in my home directory (with permissions or rwxr-x-r-x (755).)

---

### Post by fdrake on 2011-11-20
> **CharlesA said:**
> **_www-data should only have read access_**.

In my case, I changed the document root to point to a folder in my home directory (with permissions or _**rwxr-x-r-x (755)**_.)

but you have also x permissions for others (www-data). which is fine too... since www-data needs to execute the php scripts.

---

### Post by Lars Noodén on 2011-11-20
> **fdrake said:**
> @Lars Noodén
i think you should make sure that the files he is creating are accessible and executable for the user www-data since he is running a webserver. That said he should make sure that www-data is inside the webmaster group even if he is the only webmaster. and make all the files executable to the user and the group.

As pointed out above, www-data should have read access.  The default settings are enough to achieve that.  (chmod o=rx)

www-data should not be a member of the group that has write access, since that would mean that the webserver and its scripts could potentially rewrite pages and scripts.

---

