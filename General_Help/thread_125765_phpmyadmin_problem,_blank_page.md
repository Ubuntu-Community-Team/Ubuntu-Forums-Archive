---
title: "phpmyadmin problem, blank page"
date: 2006-02-04
forum: General Help
---

### Post by michaelbg on 2006-02-04
Hi,

I have successfully installed apache2, mysql and php5. 
[http://localhost](http://localhost) gives me the placeholder page (so apache2 works)
[http://localhost/testphp](http://localhost/testphp) gives me the long detailed page about php, so the php5 /apache part works.

i can manually enter my mysql. ie. mysql --user=root --password=*** (so I think that means my mysql works, that I'm not sure about, it's the first time I've installed it in my life, but it seems to be up I can stop and start it.)

However, when I type in [http://localhost/phpmyadmin](http://localhost/phpmyadmin), I just get a blankscreen. nothing happens even with an F5 refresh. In my var/www directory, I see the phpmyadmin symbolic link to /usr/share/phpmyadmin. I changed the owner and group of the link to www-data (since that seemed to be key for getting my testphp.php working).  

Still nothing though. Any idea what I should check next?

Thanks,
Michael

---

### Post by Horndog on 2006-02-04
Did you edit the config fill in phpmyadmin to connect to MySQL? Also you can see if it's running by looking at the system monitor.

---

### Post by michaelbg on 2006-02-05
Hi,

I read over the config file and noticed that the authorisation was set on by default, which of course, meant that I had to put in the right root password.
damn. So now I see the phpmyadmin page. which is fine.

BTW, I still don't see phpmyadmin or anything like that in the system monitor or in the ps output.  

I must admit I'm not used to this web configuration world.  It doesn't seem to be a world with meaningful error messages.  ie. it would have been nice if "Password incorrect" had appeared instead of just a blank page.

Anyways, my new issue is trying to understand why /etc/init.d/apache2 start doesn't work and yet apache2ctl start does...wierd. but I'll start a new thread tomorrow if I don't figure out by then. thanks for the help.

Michael

---

### Post by michaelbg on 2006-02-05
I spoke a little too quickly. Excited I guess.

the phpmyadmin page comes up, but it doesn't actually work.

ie. when I select the mysql table, it says in the lower left:
Not Found

The requested URL /phpMyAdmin/left.php was not found on this server.
Apache/2.0.54 (Ubuntu) PHP/5.0.5-2ubuntu1.1 Server at localhost Port 80

so I'm not sure what the problem is right at the moment.  left.php is in /usr/share/phpmyadmin, and  /var/www/phpmyadmin points to that directory, so I would have thought that it could find left.php.  I'm not sure what to do next.  

Michael

Update:
Oddly, when I run the mouse cursor over a command, (for example: save server_status), and type in the line
[http://localhost/phpmyadmin/server_status.php?lang=iso-en-8859-1&server=1](http://localhost/phpmyadmin/server_status.php?lang=iso-en-8859-1&server=1) into firefox, it works fine, 
but when I click on the link, a new page pops up with 
Not Found

The requested URL /phpMyAdmin/server_status.php was not found on this server.
Apache/2.0.54 (Ubuntu) PHP/5.0.5-2ubuntu1.1 Server at localhost Port 80

---

### Post by Horndog on 2006-02-05
It would appear that MySQL is not running. Try to find the error log for MySql and post the relevant parts. Also, were and how did you install MySQL? Nothing fancy just the link will do.

---

