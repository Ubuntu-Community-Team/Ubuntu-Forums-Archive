---
title: "add user folder to appache (webserver)"
date: 2010-05-13
forum: General Help
---

### Post by vebaev on 2010-05-13
Hi All,
I unpacked a mail system in my local folder /home/user/mail (with 777 chmodded)
How to add this folder to appache and be visible via brouser like [http://server/mail](http://server/mail)

I set in httpd.conf

Alias /mail/ /home/user/mail/
<Directory "/mail/">
AllowOverride AuthConfig
Options MultiViews
Order allow,deny
Allow from all
</Directory>

But I got forbidden

Thanks!

(PS: Im a newbie in appache, I just saw this lines and add them, so Im not so sure what Im doing :lol: )

---

### Post by LoneWolfJack on 2010-05-13
```

<VirtualHost *:80>
	DocumentRoot /home/user/
	<Directory />
		Options Indexes FollowSymLinks MultiViews
		AllowOverride None
		Order allow,deny
		Allow from all
	</Directory>
	<Directory /home/user/mail/>
		Options Indexes FollowSymLinks MultiViews
		AllowOverride None
		Order allow,deny
		Allow from all
	</Directory>
</VirtualHost>

```

modify settings as you wish.

don't forget to restart apache after updating the config file.

---

### Post by vebaev on 2010-05-13
Great This works! Thanks a lot! :popcorn:

---

