---
title: "configure apache to work with Eclipse and PDT"
date: 2011-06-21
forum: General Help
---

### Post by nethero on 2011-06-21
I have apache and php installed on my machine.  I'm trying to develop a php webpage using Eclipse and the PDT plugin.  I wrote a simple php file and when I select run as "PHP Web Page" in Eclipse it generates the URL [http://localhost/phpBeginner/index.php](http://localhost/phpBeginner/index.php) and the webpage displayed is...

```
Not Found

The requested URL /phpBeginner/index.php was not found on this server.
Apache/2.2.17 (Ubuntu) Server at localhost Port 80
```

How do I get my webpages developed in Eclipse to work on Apache?  Apache and PHP are working because when I put this file directly in /var/www it works indicating that Apache and PHP are capable of producing the web page.  I'm certain it has something to do with how Apache is configured but I can't figure out what it could be.  Thanks.

---

### Post by terrykiwi83 on 2011-06-21
Apache usually stores its webpages in /var/www I think so it would be a start to put the php files in there

what happens when you go to [http://localhost](http://localhost) ?

---

### Post by Dangertux on 2011-06-22
You either need to place the scripts in /var/www (or a subdirectory of)

Or create a site (formerly known as virtual host) in apache2. Note that requires you set up an alternate DNS and or alternate listening port for the specific site. You can google more about that , it is relatively simple for a more detailed explanation feel free to PM me.

---

### Post by nethero on 2011-06-22
Got it working.  Here's what I did.  I opened  /etc/apache2/sites-available/default in gedit and changed the DocumentRoot /var/www to DocumentRoot /home/<username>/workspace (this is the location of my project files).  I also had to change /var/www/ to /home/<username>/workspace/ in another part of that file.  I restarted apache by typing

```
sudo  /etc/init.d/apache2 reload
```

The when I ran it as a "PHP web page" I got a forbidden error.  I took it to mean that apache did not have read permissions on one of the directories in the path /home/<user>/workspace/.  When I typed ls -l on my command prompt at my home directory I found that it was rwx------.  indicating that only I could read write or execute.  I typed...

```
sudo chmod 755 /home/<user> 
```

and I was able to run "PHP web page" in Eclipse with no other errors.

---

