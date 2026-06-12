---
title: "Redirect www.domain.com to domain.com"
date: 2010-04-19
forum: General Help
---

### Post by Jackson024 on 2010-04-19
I am pretty new at linux but I can get around and google most everything. But I am using 9.10 as a web server running apache2. I am trying to redirect [www.domain.com]("http://www.domain.com") to doamin.com. The way it is set up now, if you go to domain.com, wow you get a awesome website. However if you go to [www.domain.com]("http://www.domain.com") you get a page cannot be displayed. I used a CNAME with my host to point to doamin.com but I rather do it myself. I tired to edit my apache2.conf and add 
```
Options +FollowSymLinks
RewriteEngine on
RewriteCond %{HTTP_HOST} .
RewriteCond %{HTTP_HOST} !^your-domain.com\.com
RewriteRule (.*) your-domain.com/$1 [R=301,L]
```
 
Then when I restart apache I get:
```
 * Starting web server apache2                                                  Syntax error on line 239 of /etc/apache2/apache2.conf:
Invalid command 'RewriteEngine', perhaps misspelled or defined by a module not included in the server configuration
                                                                         [fail]

```
 
Once I comment out the code I can start it back up fine. Anyone have any idea what is wrong or if I am even doing it right?
 
Thanks,
Jackson

---

### Post by Untitled_No4 on 2010-04-19
Try the following:

```
sudo a2enmod rewrite
sudo /etc/init.d/apache2 restart
```

---

### Post by Jackson024 on 2010-04-19
Thanks, that worked like a charm.

---

### Post by Jackson024 on 2010-04-19
Another question about this if I may?  Now when going to domain.com it just shows as [http://doamin.com](http://doamin.com), is there a way to force it to display the www?

---

### Post by Untitled_No4 on 2010-04-19
This is an issue of how apache was set up. I assume this is either your own computer or a VPS?

In terminal:
```
cd /etc/apache2/sites-available
sudo cp default domain
```
(change domain to your domain, no need for com or whatever, and actually you can name it whatever you want, but change accordingly below)
```
sudo nano domain
```

This file should look something like that:
```

<VirtualHost *:80>
	ServerAdmin webmaster@localhost

	DocumentRoot /var/www
	<Directory />
		Options FollowSymLinks
		AllowOverride None
	</Directory>
	<Directory /var/www/>
		Options Indexes FollowSymLinks MultiViews
		AllowOverride None
		Order allow,deny
		allow from all
	</Directory>
.
.
.

```
(the file is longer, but the rest is not important for us here)
Add a line under ServerAdmin as such:
```

ServerAlias www.domain.com

```

then change the directory in the next line (DocumentRoot) and also in <Directory /var/www/>

save the file (ctrl + x, then y for yes) and run
```
sudo a2ensite domain
sudo /etc/init.d/apache2 reload
```

change domain to the name of the file.

Try now?

---

### Post by Jackson024 on 2010-04-19
I am running the server version of ubuntu on my own system.
 
I am not sure what I need to change the path to for DocumentRoot and <Directory ...> My files for the site are in /var/www. But I made the changes leaving /var/www the same and now when going to [www.domain.com]("http://www.domain.com") back to page cannot be displayed. So it looks like ti stopped the redirect?
 
[COLOR=black][FONT=Verdana]Also thank you very much Untitled_No4, you've very helpful and seem extremely knowledgeable.[/FONT][/COLOR]

---

### Post by Untitled_No4 on 2010-04-19
The way I understand it you want [www.domain.com](www.domain.com) to redirect to domain.com, but also be able to show www in the URL. This is somewhat a contradiction, since [www.domain.com](www.domain.com) takes you to domain.com. Probably what happens now is that Apache is a confused, what is it supposed to do when you go to [www.domain.com?](www.domain.com?) Display it or redirect it?

Basically the right way is not to redirect www to non-www (or vice-versa) but to have both [www.domain.com](www.domain.com) and domain.com point to the correct IP address. This needs to be set up with your domain registrar. You can check if that's the case by pinging both address (ping DOMAIN_URL in terminal).

Then you need to set up your server to tell it that both www and no-www point to the same document root.

Debian and its offsprings work differently than other distributions. In Debian you hardly ever need to edit your apache2.conf. Instead you need to go to /etc/apache2/sites-available and create a virtual host for your site. The changes I've asked you to do in my previous post still apply but instead of having
```
ServerAlias www.domain.com
```
you should have
```
ServerAlias domain.com
```
this tells apache that all requests that end with .domain.com refer to the documents in a specific directory (/var/www by default), so it doesn't matter if you put www or not.

Then when you run a2ensite [FILENAME] it creates a symlink to the file you have just created to /etc/apache2/sites-enabled and when you reload apache it uses all the files under this folder as configuration files. To disable a site you run a2dissite [FILENAME] which deletes the symlink and then you need to reload apache.

and if your index file (Document Root) resides in /var/www, you do not need to change the directory at all.

So... if I were you that's what I would do:
1. Go back to apache2.conf and comment out any changes you have done by adding # to the beginning of the lines you have added.
2. Edit /etc/apache2/default to have 
```
ServerAlias domain.com
```
and the directory where your index file is located (my guess /var/www)
3. Restart apache (not reload since I don't know what changes you've made)
4. Try again

EDIT: clearing things that don't make sense...

---

### Post by Jackson024 on 2010-04-19
Thanks for explaining.  So I've commented out the changes I made to apache2.conf and added just the domain.com to domain.conf and they are working fine.  The main reason I was wanting the redirect is because I guess I'm OCD.  Like going to [http://google.com](http://google.com) is going to change to [http://www.google.com](http://www.google.com)  I did not know if that was an apache setting I could correct or not.  Now for me going to domain.com or [www.domain.com](www.domain.com) work fine, but will show as either, it will not change domain.com to [www.domain.com](www.domain.com)

---

### Post by Untitled_No4 on 2010-04-19
Things are clear now! 
Back to your first post, I think what you did is redirect www to non-www. Anyway, let's cut a long story very short.

In your document root (/var/www) create a file called .htaccess (note the dot!) and then edit add the following to the file:
```
Options +FollowSymLinks 
RewriteEngine on
RewriteCond %{HTTP_HOST} .
RewriteCond %{HTTP_HOST} !^domain\.com
RewriteRule (.*) http://domain.com/$1

```

No need to restart or reload anything as long as your mod rewrite is still enabled.

---

### Post by Untitled_No4 on 2010-04-19
Oops, wrong code. Here's what you need:
```
Options +FollowSymLinks 
RewriteEngine on 
RewriteCond %{HTTP_HOST} ^domain.com
RewriteRule ^(.*)$ http://www.domain.com/$1

```

---

### Post by Jackson024 on 2010-04-19
Perfect, that was it... thank you so much for your help.

---

