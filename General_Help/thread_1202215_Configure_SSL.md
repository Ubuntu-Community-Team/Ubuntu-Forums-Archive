---
title: "Configure SSL"
date: 2009-07-02
forum: General Help
---

### Post by mthalis on 2009-07-02
I installed apache2 in my machine now i want to enable ssl. I surfed Internet but couldn't get good idea in Ubuntu 9.04. Please help me. How to configure it from begging to advance.

Thank You

---

### Post by mthalis on 2009-07-02
Any Suggestion?

---

### Post by trojanfoe on 2009-07-02
It should have an SSL config ready and just waiting to be enabled.  Try:

```

$ sudo bash <enter your password>
# a2ensite default-ssl
# /etc/init.d/apache2 restart

```

I think that should get you closer.

---

### Post by mthalis on 2009-07-02
How can I renew certification keys?

---

### Post by trojanfoe on 2009-07-02
from 'zmore /etc/ssl/README.gz'

```

Enabling SSL
------------

To enable SSL, type (as user root):

	a2ensite default-ssl
	a2enmod ssl

If you want to use self-signed certificates, you should install the ssl-cert
package (see below). Otherwise, just adjust the SSLCertificateFile and
SSLCertificateKeyFile directives in /etc/apache2/sites-available/default-ssl to
point to your SSL certificate. Then restart apache:

	/etc/init.d/apache2 restart

```

Furthermore:

```

root@pandora:/etc/ssl# dpkg --listfiles ssl-cert
/.
/usr
/usr/sbin
/usr/sbin/make-ssl-cert
/usr/share
/usr/share/lintian
/usr/share/lintian/overrides
/usr/share/lintian/overrides/ssl-cert
/usr/share/ssl-cert
/usr/share/ssl-cert/ssleay.cnf
/usr/share/doc
/usr/share/doc/ssl-cert
/usr/share/doc/ssl-cert/README
/usr/share/doc/ssl-cert/copyright
/usr/share/doc/ssl-cert/changelog.gz
/usr/share/man
/usr/share/man/man8
/usr/share/man/man8/make-ssl-cert.8.gz

```

You can probably re-run /usr/sbin/make-ssl-cert

---

### Post by mthalis on 2009-07-02
After enabling ssl and run my project then Firefox issue below error massage.
> Secure Connection Failed  
An error occurred during a connection to 192.168.20.253.
SSL received a record that exceeded the maximum permissible length.
(Error code: ssl_error_rx_record_too_long)


Without enabling ssl work fine. How can i solve it.

---

### Post by mthalis on 2009-07-02
Configuration error or any other thing?

---

### Post by alphacrucis2 on 2009-07-02
> **mthalis said:**
> Configuration error or any other thing?

Did you create a certificate?

---

### Post by trojanfoe on 2009-07-02
Are you serving SSL on port 443?  Please post your config.

---

### Post by mthalis on 2009-07-02
Below i attached apache2.conf and ports.conf

---

### Post by trojanfoe on 2009-07-02
And the configuration for 'default-ssl' (in /etc/apache2/sites-available) ?

EDIT: plus you do have the SSL module enabled?  (a2enmod ssl)?

---

### Post by mthalis on 2009-07-02
Inside /etc/apache2/sites-available contain below two files.
yes I enabled it.

---

### Post by trojanfoe on 2009-07-02
Try adding 'Listen 443' as the first line in default-ssl.

In my config I also have SSLCertificateKeyFile commented-out.

Also I am not using the snakeoil certs, but rather generated my own using something like:

```

openssl req -new -x509 -days 365 -keyout /etc/ssl/private/server.key -out /etc/ssl/private/server.crt

```

---

### Post by mthalis on 2009-07-02
I used other program call **webmin ** using ssl
> [https://ites-desktop:10000/](https://ites-desktop:10000/)( work properly)
so please help me what is wrong. Without ssl my program work fine after enable ssl mode in my program it gave error massage. please help me.

I did what you say but same problem.

---

### Post by trojanfoe on 2009-07-02
Sorry I don't have any more answers for you.

---

### Post by mthalis on 2009-07-02
Any answer?

---

