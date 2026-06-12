---
title: "apache GUI"
date: 2006-06-13
forum: General Help
---

### Post by jethro10 on 2006-06-13
Hi,
I've just installed apache2 web server. My familiarity is unfortunatley with Ms Internet server.

I'm struggling, can anyone tell me of a GUI that works on gnome for administering this web server. 
Preferably not Webmin as i've spent aged to not get this to work, unless someone has a deb version of it, as the rpm would not alien for me.

ThanksJeff

---

### Post by Ctrl+Alt+Del on 2006-06-13
haven't tried it myself, but [http://everythinglinux.org/Mohawk/index.html](http://everythinglinux.org/Mohawk/index.html) might do the job

---

### Post by jethro10 on 2006-06-13
[QUOTE=Ctrl+Alt+Del]haven't tried it myself, but [http://everythinglinux.org/Mohawk/index.html](http://everythinglinux.org/Mohawk/index.html) might do the job[/QUOTE]

Yeah, seen that one, but the Author says its a dead project.

Any more anyone?

J

---

### Post by dabang on 2006-06-13
Have you tried configuring apache via editing the conf-files? It isn't that hard - well, depending on what you want tot do with apache ;) . Maybe you could tell us what your specific problem is? I've set up apache a few times, but only as a local server for web development, so I'm no expert...

---

### Post by jethro10 on 2006-06-13
[QUOTE=dabang]Have you tried configuring apache via editing the conf-files? It isn't that hard - well, depending on what you want tot do with apache ;) . Maybe you could tell us what your specific problem is? I've set up apache a few times, but only as a local server for web development, so I'm no expert...[/QUOTE]
I'm starting to think your right, i've spent more time looking for an easy to use tool that it would have taken to learn how to edit manually.

However thats not the point for me. I'm trying really hard to justify how i could replace our stuff at work with linux. With windows servers  even when you dont do stuff often, the nice GUI is easy to pick up and 'remember', which is usefull to us as were are really all-rounders and sometimes dont touch a particular subject for a year. SME's where IT people have to be all rounders are not catered for very well in Linux i'm afraid.

J

---

### Post by shakin on 2006-06-13
[QUOTE=jethro10]I'm starting to think your right, i've spent more time looking for an easy to use tool that it would have taken to learn how to edit manually.

However thats not the point for me. I'm trying really hard to justify how i could replace our stuff at work with linux. With windows servers  even when you dont do stuff often, the nice GUI is easy to pick up and 'remember', which is usefull to us as were are really all-rounders and sometimes dont touch a particular subject for a year. SME's where IT people have to be all rounders are not catered for very well in Linux i'm afraid.

J[/QUOTE]

1. I think webmin will install easily using the tar.gz download from webmin.com. I did that with Warty and it worked great.

2. Try [http://www.apache-gui.com/](http://www.apache-gui.com/) and see if that works. I don't know anything about the product.

I will also try to refute your claim that most IT people can't configure Apache. Once you learn how Apache on Debian works it's very easy. I only touch Apache configuration a few times a year and yet I don't have a problem.

The main config directory is /etc/apache2

Most configuration is done in individual virtual hosts. If you only run one web site then you don't need to create any. Your default web site is configured in the file /etc/apache2/sites-available/default

If you do need to make a second web site on that server then just copy the default file and save as your new site name. You'll need to adjust the second line of the file so the asterix (*) becomes your site name ([www.sitename.com)](www.sitename.com)).

In the default file (or the file for each other web site) you really only need to change path to the web site's files. Change the DocumentRoot setting (default is /var/www) and the second Directory setting. Both point to the same path (eg <Directory /var/www> becomes <Directory /var/www/sitename> or whatever you set the DocumentRoot to).

That's all it takes to setup your web site. If you only run a single web site you don't need to change anything. When you install PHP or mod_perl, dpkg will take care of Apache setup when you install the package, so you hardly ever have to worry about advanced setup options.

---

### Post by jethro10 on 2006-06-13
[QUOTE=shakin]1. I think webmin will install easily using the tar.gz download from webmin.com. I did that with Warty and it worked great.

2. Try [http://www.apache-gui.com/](http://www.apache-gui.com/) and see if that works. I don't know anything about the product.

I will also try to refute your claim that most IT people can't configure Apache. Once you learn how Apache on Debian works it's very easy. I only touch Apache configuration a few times a year and yet I don't have a problem.

The main config directory is /etc/apache2

Most configuration is done in individual virtual hosts. If you only run one web site then you don't need to create any. Your default web site is configured in the file /etc/apache2/sites-available/default

If you do need to make a second web site on that server then just copy the default file and save as your new site name. You'll need to adjust the second line of the file so the asterix (*) becomes your site name ([www.sitename.com)](www.sitename.com)).

In the default file (or the file for each other web site) you really only need to change path to the web site's files. Change the DocumentRoot setting (default is /var/www) and the second Directory setting. Both point to the same path (eg <Directory /var/www> becomes <Directory /var/www/sitename> or whatever you set the DocumentRoot to).

That's all it takes to setup your web site. If you only run a single web site you don't need to change anything. When you install PHP or mod_perl, dpkg will take care of Apache setup when you install the package, so you hardly ever have to worry about advanced setup options.[/QUOTE]

Thanks, some of this helps a lot.
I will give it a go.
I seem to have a web site working now, the problem I now have is setting an Alias to another directory on another hard disk
the:-
Alias /MoreFiles/ "/SomeExtraSpace/"
does not seem t oget recognised.

Jeff

---

### Post by jethro10 on 2006-06-13
Ok, getting there.
However I gather I need to stop and re-start the site but I get this error message on startin and similar on stopping :-

```
apache2: Could not determine the server's fully qualified domain name, using 127.0.0.1 for ServerName
(13)Permission denied: make_sock: could not bind to address [::]:80
no listening sockets available, shutting down
Unable to open logs
```

This is also the snipped from the top of my default config file 
```

NameVirtualHost *
<VirtualHost *>
	ServerAdmin webmaster@localhost
	
	DocumentRoot /home/jeff/WebSite
	<Directory />
		Options FollowSymLinks
		AllowOverride None
	</Directory>
	<Directory /home/jeff/WebSite/>
		Options Indexes FollowSymLinks MultiViews
		AllowOverride None
		Order allow,deny
		allow from all
		# Uncomment this directive is you want to see apache2's
		# default start page (in /apache2-default) when you go to /
		#RedirectMatch ^/$ /apache2-default/
	</Directory>

```
I was hoping it would point to a directory in my home area, but I believe its the Stop/Start bit at fault?

PS: how do you pick a default page to open, eg "default.html"
Jeff

---

### Post by jethro10 on 2006-06-14
Well I can confirm its the start/stop bit at fault because a re-boot picked up the correct webroot.

can anyone advise?

Jeff

---

### Post by blkish on 2006-06-14
[QUOTE=jethro10]I'm starting to think your right, i've spent more time looking for an easy to use tool that it would have taken to learn how to edit manually.

However thats not the point for me. I'm trying really hard to justify how i could replace our stuff at work with linux. With windows servers  even when you dont do stuff often, the nice GUI is easy to pick up and 'remember', which is usefull to us as were are really all-rounders and sometimes dont touch a particular subject for a year. SME's where IT people have to be all rounders are not catered for very well in Linux i'm afraid.

J[/QUOTE]

You might like to consider other distributions in your planning if you're thinking of migrating from a windows infrastructure. in my experience of weaning SMEs off MS, as you correctly point out, a nice reliable GUI is absolutely crucial.
webmin performs this role beautifully, especially with the 'Stress Free Tiger' theme from [http://www.stress-free.co.nz/content/view/141/2/](http://www.stress-free.co.nz/content/view/141/2/)

i would recommend looking into CentOS (binary compatible RedHat EL rebuild) which has excellent community support and build quality (like Ubuntu). there is a webmin package available from the 'Dag Wieers' repository for this distribution.

the main thing preventing me from moving to Ubuntu as a default-choice server platform is the availability of Webmin as a distribution-specific package. i've posted a thread asking whether there is likelihood of a package anytime soon and will let you know the outcome.

cheers blkish

---

### Post by jethro10 on 2006-06-14
[QUOTE=blkish]You might like to consider other distributions in your planning if you're thinking of migrating from a windows infrastructure. in my experience of weaning SMEs off MS, as you correctly point out, a nice reliable GUI is absolutely crucial.
webmin performs this role beautifully, especially with the 'Stress Free Tiger' theme from [http://www.stress-free.co.nz/content/view/141/2/](http://www.stress-free.co.nz/content/view/141/2/)

i would recommend looking into CentOS (binary compatible RedHat EL rebuild) which has excellent community support and build quality (like Ubuntu). there is a webmin package available from the 'Dag Wieers' repository for this distribution.

the main thing preventing me from moving to Ubuntu as a default-choice server platform is the availability of Webmin as a distribution-specific package. i've posted a thread asking whether there is likelihood of a package anytime soon and will let you know the outcome.

cheers blkish[/QUOTE]


Thanks
J

---

