---
title: "wordpress installation on ubuntu"
date: 2011-12-08
forum: General Help
---

### Post by gacy on 2011-12-08
Dear all,
With the aim to create a blog site -- in this thread i am using my.blogsite.name to indicate the url -- I downloaded and extracted wordpress   in /usr/share/wordpress. 
 
I issued the command
 
$me: ln -s /usr/share/wordpress /var/www/my.blogsite.name/wordpress
 
Then I used the command to create a virtualhost in /etc/apache2/sites-available/
 
<VirtualHost * >
        ServerAdmin [EMAIL="myemail@email.com"]myemail@email.com[/EMAIL]
        ServerName my.blogsite.name
         DocumentRoot /var/www/my.blogsite.name
        
    <Directory /var/www/my.blogsite.name/>
            Order Deny,Allow
            Allow from all
            Options -Indexes
      </Directory>
</VirtualHost>

Finally I run
$me: /etc/init.d/apache2 restart
 
When I open a web browser I can see the "It Works" default message on the my.blogsite.name but when I try to actually install wordpress by going at [http://my.blogsite.name/wordpress/wp-install/install.php](http://my.blogsite.name/wordpress/wp-install/install.php) I get the 404 error message page not found.
 
Any ideas? What am I doing wrong?

---

### Post by lisati on 2011-12-08
Did you remember to use *a2ensite* to activate the site?

---

### Post by gacy on 2011-12-08
hmm...No, i didn't. OK I will do that and see what happens.
Thanks.

---

### Post by gacy on 2011-12-09
i tried it, and still the same problem...any other suggestions?

---

### Post by lisati on 2011-12-09
> **gacy said:**
> i tried it, and still the same problem...any other suggestions?

You have to restart/reload apache after using a2ensite

---

### Post by gacy on 2011-12-09
OK it is SOLVED!
:KS

---

