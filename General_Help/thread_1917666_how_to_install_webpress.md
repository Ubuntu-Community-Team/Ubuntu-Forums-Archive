---
title: "how to install webpress"
date: 2012-01-30
forum: General Help
---

### Post by YigalB on 2012-01-30
I was trying to install webpress, following the guide lines from: [https://help.ubuntu.com/community/WordPress](https://help.ubuntu.com/community/WordPress) 

After Apache restart the browser didn't load the  "http://localhost/wordpress"

AI would appreciate your help.

---

### Post by sanderd17 on 2012-01-30
Does [http://localhost](http://localhost) gives you something?

---

### Post by YigalB on 2012-01-30
I forgot to mention that the error message is:
Error establishing a database connection

---

### Post by sanderd17 on 2012-01-30
That's the error you see in your browser?

---

### Post by josephmills on 2012-01-30
you need to create a mysql data base to store all the info. 

You could use phpMyAdmin (sudo apt-get install phpmyadmin)for this if you like. 
Next you need to tell wordpress how to find the mysql tables 
open wp-config.php. it is somewhere by /var/www/wordpress/wp-content  or wp-admin something like that. fill out the  right info and then reload apache and mysql and you should be good to go.

---

### Post by sanderd17 on 2012-01-30
> 
```
sudo bash /usr/share/doc/wordpress/examples/setup-mysql -n wordpress localhost
```

Note: (Use sh instead of bash for Feisty or earlier.) This script creates the MySQL database and user wordpress for the new MySQL database named localhost (that will be used for WordPress). If you will be hosting a virtual host and/or already know your URL, it is best to name your database the same as your URL. Also if you plan on hosting multiple blogs with different virtual hosts, each needs a differently named database, which would be achieved in the same way. For example, if your URL is wordpress.mydomain.org, then the command would be 


This should have created the right database before the op opened the browser. Isn't it better to retry to execute this cript instead of manually changing things?

---

### Post by josephmills on 2012-01-30
ok here is some more details here [HOW TO INSTALL WORDPRESS ON UBUNTU ](http://www.jonathanmoeller.com/screed/?p=3370)

---

### Post by YigalB on 2012-01-30
> **sanderd17 said:**
> Does [http://localhost](http://localhost) gives you something?
Yes: it gives the:
> It works!

This is the default web page for this server.

The web server software is running but no content has been added, yet.

I also use it with code I have at /var/www

---

### Post by josephmills on 2012-01-30
> **sanderd17 said:**
> This should have created the right database before the op opened the browser. Isn't it better to retry to execute this cript instead of manually changing things?

1st thing is 1st ubuntu does not use bash it uses dash so you might want to change that 1st. see part 9 Change The Default Shell
  [HERE](http://www.howtoforge.com/perfect-server-ubuntu-11.10-ispconfig-3-p3)

---

### Post by sanderd17 on 2012-01-30
> **josephmills said:**
> 1st thing is 1st ubuntu does not use bash it uses dash so you might want to change that 1st. see part 9 Change The Default Shell
  [HERE](http://www.howtoforge.com/perfect-server-ubuntu-11.10-ispconfig-3-p3)

I only got this from the site the OP was following. The ubuntu help pages.

So I suppose those help pages should be edited.

---

### Post by josephmills on 2012-01-30
> **sanderd17 said:**
> I only got this from the site the OP was following. The ubuntu help pages.

So I suppose those help pages should be edited.

LOL yup there for 6.06 we are at 12.04 almost double. follow the link that I sent and you will do fine.

---

### Post by YigalB on 2012-01-30
> **josephmills said:**
> ok here is some more details here [HOW TO INSTALL WORDPRESS ON UBUNTU ](http://www.jonathanmoeller.com/screed/?p=3370)
Thanks, but I don't think I am going to go through  so many stages.
I have LAMP installed and working - such a long installation process is not friendly and secure.

I would rather give up using wordpress. Seems not ready to be deployed for Ubuntu.

---

