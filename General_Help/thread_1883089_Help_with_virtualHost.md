---
title: "Help with virtualHost"
date: 2011-11-18
forum: General Help
---

### Post by davidtheo on 2011-11-18
Why do I get an error when runing

sudo /etc/init.d/gdm stop
or
sudo /etc/init.d/kdm stop 


The error is 
```

sudo: /etc/init.d/gdm: command not found

```

Also

No matter what I try I can not get a virtualHost working.

Why do I get an error when runing

sudo /etc/init.d/gdm stop
or
sudo /etc/init.d/kdm stop


The error is
```

sudo: /etc/init.d/gdm: command not found

```

Also

No matter what I try I can not get a virtualHost working.
- 	
If I so to localhost/testphp.php I get the php config info ( that is right php is working)

If I go to localhost/strood/public the zend page displays ( that is right )

BUT if I just go to l127.0.1.2 I get the error below

**Internal Server Error**

The server encountered an internal error or misconfiguration and was unable to complete your request.
Please contact the server administrator, [email]admin@site.com[/email] and inform them of the time the error occurred, and anything you might have done that may have caused the error.
More information about this error may be available in the server error log.



/etc/hosts
```

127.0.0.1 localhost
127.0.1.1 ubuntu.ubuntu-domain ubuntu
127.0.1.2 site

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters

```

/etc/apache2/httpd.conf
```

NameVirtualHost 127.0.1.2:80

```

/etc/apache2/sites-available/site.com
```

<VirtualHost 127.0.1.2:80>
ServerName site.com
ServerAlias site.com
ServerAdmin admin@site.com
DocumentRoot /var/www/folder/public
<Directory /var/www/folder/public/>
Options FollowSymLinks
AllowOverride All
Order allow,deny
allow from all
</Directory>
</VirtualHost>


```

---

### Post by matt_symes on 2011-11-18
Hi

To answer your fist question, 11.10 no longer uses GDM but lightdm.

```
sudo service lightdm stop
```Might be an idea to remove the references to your business in the second part of your post if indeed that is what they are.

Kind regards

---

### Post by nothingspecial on 2011-11-18
> **matt_symes said:**
> ]Might be an idea to remove the references to your business in the second part of your post if indeed that is what they are.

Kind regards

I've snipped the lot out just in case. I (or another staff) can put it back if you want. Just trying to be safe. Apologies if it is an inconvenience.

---

### Post by davidtheo on 2011-11-18
> **nothingspecial said:**
> I've snipped the lot out just in case. I (or another staff) can put it back if you want. Just trying to be safe. Apologies if it is an inconvenience.

Hi nothingspecial

That second part was the more important part, it is not my business  but an site I am building free for my friend and I need the vhosts working right before I can start it. The web site is an free ( non money making site ).

---

### Post by nothingspecial on 2011-11-18
I've put it back but edited the sensitive parts ie the admin name and domain name for now.

If you would prefer the original that's fine.

---

