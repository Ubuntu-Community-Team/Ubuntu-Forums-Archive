---
title: "Website Hosting From my home computer?"
date: 2011-02-17
forum: General Help
---

### Post by BSG Fan on 2011-02-17
Hey guys,

I have three questions using Linux...

1- How can I prepare my own website in my own pc at home?  Any idea and steps?  I have had used Nvu in the past, but it looked to me very unstable (it disappeared from my screen at simple use, despite re-installing it again and again), and I think the Kompozer was also not very far from it, my experience.


2- How can I prepare my pc to run that website?  What Linux software I need to download for?  Do I really need to have a great cash to transform my poor pc into it?  I think that because it is Linux-Ubuntu, not Windows, the situation can not be any worst or more expensive... uh?

3- In theory, if I have that website in my own pc... how I know that hackers can _**only see**_ my page (in a separate-isolated folder from other folders, right?) and can not take a *tour* of my entire pc, documents, photos, etc, including copying or stealing archives or Ooo documents?  It is not that the same way when (by example) a hacker can steal the next Stephen King book or script and sell/display it worldwide without even his knowledge?

Thanks in advance.
=/

---

### Post by jwcalla on 2011-02-17
You can install a webserver like apache2 and then all of the public documents would be stored in a separate folder on the filesystem, typically /var/www.  Of course you'll have to open up port 80 on your firewall so the public can access your computer.

You'll have to get a static IP from your ISP and register it with a domain name so the public can resolve your website name to an IP address.

---

### Post by pqwoerituytrueiwoq on 2011-02-17
> **jwcalla said:**
> You can install a webserver like apache2 and then all of the public documents would be stored in a separate folder on the filesystem, typically /var/www.  Of course you'll have to open up port 80 on your firewall so the public can access your computer.

You'll have to get a static IP from your ISP and register it with a domain name so the public can resolve your website name to an IP address.
you can use dyndns.com to get a free sub domain name and not need a static ip
if your ip changes the site may go down for a few minutes till the ip gets updated again
if you plan on using php you will need to install it 
you may want to edit php.ini (/etc/php5/apache2/php.ini)
and enable it to show errors so you don't keep saying wtf at a blank page 
around line 531
you may also want to enable .htaccess (/etc/apache2/sites-available/default)
code segmet
```
    <Directory /var/www/>
        Options Indexes FollowSymLinks MultiViews ExecCGI
        AllowOverride All
        Order allow,deny
        allow from all
    </Directory>
```
and my fire wall i assume you mean forward port 80
you should set a static ip on the server machine

---

### Post by BSG Fan on 2011-02-18
Users "jwcalla" and "pqwoerituytrueiwoq"
Thanks a lot for your respective replies and suggestions.  Although I do not understand the terminology you both used I will study the terms later.
I think it seems some kind of complicated... But i won't surrender.
:)

---

### Post by WorMzy on 2011-02-18
For 1 & 2:
[LIST][*]Firstly, install LAMP.
```
sudo apt-get install lamp-server^
```

[*]Next, take ownership of the /var/www folder so that you can add/edit/delete files there.
```
sudo chown $USER /var/www
```

[*]Next, open your favourite text editor (e.g. Gedit, Vim, etc) and start writing html. Use [http://www.w3schools.com/](http://www.w3schools.com/) if you're not sure how to.


Alternatively, download and install a WYSIWYG editor, like Amaya, BlueGriffon, etc.


[*]Finally, browse to [http://localhost]("http://localhost") to see your webpages.[/LIST]

For 3: Just make sure that the www-data user and group do _not_ have read access to any folder other than the /var/www folder and you should be fine.

---

### Post by BSG Fan on 2011-02-19
> **WorMzy said:**
> For 1 & 2:
[LIST][*]Firstly, install LAMP.
```
sudo apt-get install lamp-server^
```

[*]Next, take ownership of the /var/www folder so that you can add/edit/delete files there.
```
sudo chown $USER /var/www
```

[*]Next, open your favourite text editor (e.g. Gedit, Vim, etc) and start writing html. Use [http://www.w3schools.com/](http://www.w3schools.com/) if you're not sure how to.


Alternatively, download and install a WYSIWYG editor, like Amaya, BlueGriffon, etc.


[*]Finally, browse to [http://localhost]("http://localhost") to see your webpages.[/LIST]

For 3: Just make sure that the www-data user and group do _not_ have read access to any folder other than the /var/www folder and you should be fine.

==
User "WorMzy"
Thanks a lot for your valuable help.  Now I have a idea
That the force accompany me,

BSG Fan
=)

---

