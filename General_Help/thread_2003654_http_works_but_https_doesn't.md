---
title: "http works but https doesn't???"
date: 2012-06-14
forum: General Help
---

### Post by AlexBooton on 2012-06-14
Hi,

I followed the instructions at [http://www.howtoforge.com/perfect-server-ubuntu-12.04-lts-apache2-bind-dovecot-ispconfig-3]("http://www.howtoforge.com/perfect-server-ubuntu-12.04-lts-apache2-bind-dovecot-ispconfig-3").

I was careful but there's always the possibility I missed a step.

Now [http://localhost](http://localhost) works fine but not [https://localhost](https://localhost).

Firefox says:
[INDENT]Secure Connection Failed
   An error occurred during a connection to localhost.
   SSL received a record that exceeded the maximum permissible length.
   (Error code: ssl_error_rx_record_too_long)[/INDENT]

IE (from the LAN) just says: "Internet Explorer cannot display the webpage"

Chrome (from the LAN) says: 
[INDENT]SSL connection error
Unable to make a secure connection to the server. This may be a problem with the server, or it may be requiring a client authentication certificate that you don't have.
[/INDENT]

I don't know if this is relevant but I notice that 12.04 doesn't appear to have an apache mod-ssl where 11.04 does.  Is there replacement for mod-ssl?

What am I missing?  Where do I look to get started?

Thanks,

AB

---

### Post by 0011235813 on 2012-06-14
> **AlexBooton said:**
> Hi,

I followed the instructions at [http://www.howtoforge.com/perfect-server-ubuntu-12.04-lts-apache2-bind-dovecot-ispconfig-3]("http://www.howtoforge.com/perfect-server-ubuntu-12.04-lts-apache2-bind-dovecot-ispconfig-3").

I was careful but there's always the possibility I missed a step.

Now [http://localhost](http://localhost) works fine but not [https://localhost](https://localhost).

Firefox says:
[INDENT]Secure Connection Failed
   An error occurred during a connection to localhost.
   SSL received a record that exceeded the maximum permissible length.
   (Error code: ssl_error_rx_record_too_long)[/INDENT]

IE (from the LAN) just says: "Internet Explorer cannot display the webpage"

Chrome (from the LAN) says: 
[INDENT]SSL connection error
Unable to make a secure connection to the server. This may be a problem with the server, or it may be requiring a client authentication certificate that you don't have.
[/INDENT]

I don't know if this is relevant but I notice that 12.04 doesn't appear to have an apache mod-ssl where 11.04 does.  Is there replacement for mod-ssl?

What am I missing?  Where do I look to get started?

Thanks,

AB
I'm not really sure, but have you tried checking the firewall? Your https port may be denied.
```
sudo ufw status verbose
```
And put the results in here.

---

### Post by kanikilu on 2012-06-14
The apache2 module is just called "ssl". Have you tried enabling that? You also need to generate self-signed certificates, and enable the default virtual host:

```
sudo make-ssl-cert generate-default-snakeoil
sudo a2enmod ssl
sudo a2ensite default-ssl
sudo service apache2 restart
```

---

### Post by AlexBooton on 2012-06-14
> **0011235813 said:**
> I'm not really sure, but have you tried checking the firewall? Your https port may be denied.
```
sudo ufw status verbose
```
And put the results in here.

Thanks for the feedback.

I haven't even enabled the firewall yet.  This is a new install.

sudo ufw says "Status: inactive"

Also, all my testing is from within the LAN so there is no issue with the firewall in the router.

Any other thoughts?

Thanks,

AB

---

### Post by |{urse on 2012-06-14
I've had this issue before, 
It would help to see your ports.conf and apache2.conf, /etc/apache2/conf.d or httpd.conf (whichever you used to configure your server.) If you post those be sure to attach them to your post in a text file so as not to flood the forums.

In my case changing the Vhost tag from

<VirtualHost server.foo.com:443> 
to
<VirtualHost _default_:443>

Fixed it, but that's a pretty well known fix for this and you've likely already tried it.

---

### Post by AlexBooton on 2012-06-14
> **kanikilu said:**
> The apache2 module is just called "ssl". Have you tried enabling that? You also need to generate self-signed certificates, and enable the default virtual host:

```
sudo make-ssl-cert generate-default-snakeoil
sudo a2enmod ssl
sudo a2ensite default-ssl
sudo service apache2 restart
```

That was it!  I don't know how I missed it but I apparently didn't do the make-ssl-cert part.

Actually I think I have a clue.  I don't have a fqdn so I think   making the certificate failed the first time.  Could that be it? 

Thank you kanikilu and thank you to all of you who offered assistance.  I greatly appreciate it.

AB

---

### Post by AlexBooton on 2012-06-14
Oops. This was a duplicate post.  Please ignore.

---

