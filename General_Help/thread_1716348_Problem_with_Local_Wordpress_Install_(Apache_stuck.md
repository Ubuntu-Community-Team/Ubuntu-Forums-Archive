---
title: "Problem with Local Wordpress Install (Apache stuck?)"
date: 2011-03-28
forum: General Help
---

### Post by demonboy on 2011-03-28
I'm having a problem installing Wordpress. One of the issues is out of date and conflicting guides: sometimes I'm told to store my wordpress folder in user/www, sometimes in user/public_html and so on. Consequently I've got myself in a mess. When I try and run the wordpress install procedure I get this:

> 
Error establishing a database connection

This either means that the username and password information in your wp-config.php file is incorrect or we can't contact the database server at root. This could mean your host's database server is down.

etc
etc


All of the details are correct. I have tried, therefore, to reset Apache but I get this message:

```

jamie@jamie-presario:~$ sudo /etc/init.d/apache2 restart
[sudo] password for jamie: 
 * Restarting web server apache2                                                [Mon Mar 28 20:15:19 2011] [warn] The Alias directive in /etc/phpmyadmin/apache.conf at line 3 will probably never match because it overlaps an earlier Alias.
 ... waiting [Mon Mar 28 20:15:20 2011] [warn] The Alias directive in /etc/phpmyadmin/apache.conf at line 3 will probably never match because it overlaps an earlier Alias.
                                                                         [ OK ]

```

My questions:

- is there a definitive guide to installing Wordpress on Maverick 10.10? All guides I'm finding are out of date.
- How do I uninstall LAMP and start all over again?

---

