---
title: "Trouble with local wordpress installation"
date: 2011-09-22
forum: General Help
---

### Post by japhyr on 2011-09-22
I am running ubuntu 10.04 desktop, php5.3, and wordpress 3.2.1. I copied the wordpress directory to /var/www/site/blog. I have set up mysql, and edited wp-config.php appropriately. But when I navigate to [http://localhost/site/blog/wp-admin/install.php](http://localhost/site/blog/wp-admin/install.php), I am only offered to save or download the install.php file. I can run php scripts in any /var/www/ directory, including /var/www/site/blog/wp-admin/.

I have been searching for a solution, but have not found anything relevant. What do I need to do in order to make the installation run?

---

### Post by Dangertux on 2011-09-22
Did you restart apache after you installed php?

Also, is your php.ini configured properly?

Did you install each package seperately or did you install the LAMP stack as a whole?

What are the permissions on your /var/www/blog folder and subsequent folders are they correct? 

This should give you a starting poinjt, if you give more details we can probably answer the question better.

---

### Post by japhyr on 2011-09-23
I did restart apache.

I haven't changed anything in php.ini.  I have not read anything about changing php.ini in any of the wordpress installation guides I have looked at.

I installed each package separately.  I have a locally hosted django site, and a site that runs some plain python (non-django) scripts.

I chmodded /var/www/blog to 777.

---

