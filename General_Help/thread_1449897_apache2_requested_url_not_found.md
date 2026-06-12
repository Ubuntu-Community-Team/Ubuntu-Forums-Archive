---
title: "apache2 requested url not found"
date: 2010-04-08
forum: General Help
---

### Post by Doin on 2010-04-08
Hi everyone, 

I looked around on the internet to find a solution, but none found.
I installed apache2 on Karmic Koala and that one works. On the default page I created a link to "/home/me/Documents/folder/index.html", but when I click the link it gives me the URL not found-error. Any help is welcome

Greetings, 

Me.

---

### Post by SnickerSnack on 2010-04-08
The default page is in /var/www, right?  So that is considered the document root, and I'd guess that when you point to "/home/me/Documents/folder/index.html", it's actually looking in "/var/www/home/me/Documents/folder/index.html".

Either that or apache2 won't let a page redirect outside of /var/www, which is a good idea for obvious security reasons.  You should just keep your files in /var/www.

---

### Post by mcduck on 2010-04-08
Like said, Apache doesn't allow that kind of redirecting.

If you want to have your web site in your home directory instead of /var/www, then you should edit Apache's configuration (in /etc/apache2) to create a web site in your home directory.

edit: if you really want to use a link, you need to make a symbolic link of the file itself (with the "ln -s" command), not a link on the HTML code. But I *really* recommend configuring the site location instead.

---

