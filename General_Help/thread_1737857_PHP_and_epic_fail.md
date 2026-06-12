---
title: "PHP and epic fail"
date: 2011-04-24
forum: General Help
---

### Post by bretteroo on 2011-04-24
I setup an Ubuntu machine today specifically for the purpose of using it for PHP development and testing.  I installed Apache, PHP, and a few other necessary modules.

Now here is the ticket.  Whenever I try to run a script, it fails, even the basic phpinfo() does not work properly.  I put it in the /var/www/ folder to test, load up Firefox, and it asks me to save or open the file, as if I was trying to download it.

Any thoughts?  Would a screenshot be helpful?

Thanks in advanced.  I am not a newbie but I am not a wizard either.

---

### Post by bretteroo on 2011-04-24
This is what happens every time I try to run a php script.

---

### Post by Zwany on 2011-04-24
try

sudo /etc/init.d/apache2 restart

---

### Post by bretteroo on 2011-04-24
No dice my friend, same error.

---

### Post by Zwany on 2011-04-24
sudo apt-get install libapache2-mod-php5 ?

then restart apache.

---

### Post by bretteroo on 2011-04-24
Already installed and I have restarted apache several times.

This is extremely frustrating for me.  I found a similar post about an issue like this on another site, but alas it helped me none.

---

### Post by terrapin893 on 2011-04-24
Generally this sort of thing is related to a MIME type.

If you're using an htaccess file try disabling it.  

Also check your httpd.conf.  Look for "add handler" and "add type" variables.

---

### Post by Baumbart on 2011-04-24
have you activated php?
```

sudo a2enmod php5        # for PHP5 or
sudo a2enmod php4        # for PHP4 

```

Then resatart server.

---

### Post by bretteroo on 2011-04-24
Yes I have activated it.  Same issue.

---

### Post by Xalltar on 2011-04-24
May I try to help you ?

I've just installed LAMP with PHPMyAdmin and Komodo Edit 6 interface using that :

[http://www.howtoforge.com/ubuntu_lamp_for_newbies](http://www.howtoforge.com/ubuntu_lamp_for_newbies)

I hope it will work for you. I've just followed every line.

I'm a REAL noob but maybe it can help you !

Good Luck !

---

### Post by WorMzy on 2011-04-24
The reason you're getting that prompt is because you're bypassing the server. You're attempting to view the file from file:///var/www, and not [http://localhost](http://localhost)

---

### Post by Baumbart on 2011-04-24
... and empty your browser's cache before trying again.

---

### Post by bretteroo on 2011-04-24
I got it to work bu stripping out apache, php, and mysql, rebooting, then reinstalling.

Thanks for all the help.

---

