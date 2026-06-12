---
title: "Creating a website with Apache2."
date: 2009-07-04
forum: General Help
---

### Post by tacosta on 2009-07-04
Good evening gentleman,

I tried finding an answer but i got overwhelmed with information and i can't get it to work, so i thought i would just post it...i apologize if it has been answered, i did use the search feature but still couldn't find it.

I recently installed Apache2 and the service is running because i open "localhost" in FF and i get the "It works!" page.

I have a folder in my desktop with a site inside and i just want to configure a new website in Apache and point to that folder.

I don't need it to be accessed by the outside, its just local so i can play around with PHP.

So...what is the fastest/simplest way of doing this? (except copy/paste to /var/www/)

Thank you for your time,
Tiago Costa

---

### Post by wojox on 2009-07-04
It's easier to put it in /var/www/

Then

```
cd /etc/apache2/sites-available/
```

And look for default file

```
ls
```

```
sudo gedit default 
```

Change to something like this

<Directory /var/www/>
Options Indexes FollowSymLinks MultiViews
AllowOverride All
Order allow,deny
allow from localhost
</Directory>
<Directory /var/www/some/other/folder/>
Options Indexes FollowSymLinks MultiViews
AllowOverride all
Order allow,deny
allow from all
</Directory>

---

### Post by tacosta on 2009-07-04
What URL or IP: Port should i type in my browser so i can view my site?

---

### Post by credobyte on 2009-07-04
You can access your website trough :

[LIST]
[*]localhost
[*]127.0.0.1
[*]your hostname ( computer name )
[/LIST]

---

### Post by SoftwareExplorer on 2009-07-04
To see what apache is serving, put ```
localhost
``` in the address bar of firefox on the computer it is running on.

Edit:Looks like I'm a little slow...

---

### Post by tacosta on 2009-07-05
Localhost gives me the "It works!" page which is the content of index.html in /var/www/.

I don't want to copy/paste my sites there because i would have to do it everytime i wanted to test a site.

I just want to configure Apache to have more than one site, for example:

Default Site -> /var/www/
Test Site 1 -> /home/user/site1/
Test Site 2 -> /home/user/site2/
(...)

I wanted to know how can i configure apache to have different websites, each pointing to a specific location and what to type on my browser to access each one of my sites...

Keep in mind that i don't need it to be accessed from the outside, the purpose is just developing in PHP.

Thank you for your time, 
Tiago Costa

---

### Post by SoftwareExplorer on 2009-07-05
What if you put a symbolic link in the WWW directory to the folder on your desktop? then it would be localhost/symlinkname to go to the site.

---

### Post by cpetercarter on 2009-07-05
I am not sure why you want to have /var/www as your default site. It is a nuisance for the sort of work which you have in mind, since it is 'owned' by root and not by 'your_user_name'. It might be much more convenient to have a default site at /home/your_user_name/www', which 'your_user_name' owns. You could write an index.html file for this site with links to sub-directories containing the different web sites which you want to use (eg <a href='my_first_site/index.html'>my first site</a>).
If you look at [https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP), about half way down there is a section entitled 'Virtual hosts'which explains how to set up a new site at /home/your_user_name/www' and how to make this the default for apache.

---

