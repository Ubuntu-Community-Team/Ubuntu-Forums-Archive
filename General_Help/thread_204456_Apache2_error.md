---
title: "Apache2 error"
date: 2006-06-27
forum: General Help
---

### Post by sirhan on 2006-06-27
Hai..

I got this message while restarting my apache2.

* Forcing reload of apache 2.0 web server... apache2: Could not determine the server's fully qualified domain name, using 127.0.0.1 for ServerName
httpd (pid 6119?) not running

Anybody know why?

---

### Post by mlind on 2006-06-27
You haven't defined fqdn on /etc/hosts ? 


If you're running apache2 just locally, here's two ways to fix it that I know

[LIST]
[*] add this to /etc/apache2/apache2.conf
```

ServerName localhost

```

[*] add localhost.localdomain to /etc/hosts as alias to 127.0.0.1. This one is discouraged.
[/LIST]

---

### Post by m23 on 2006-06-27
blah

---

### Post by sirhan on 2006-06-27
[QUOTE=mlind]You haven't defined fqdn on /etc/hosts ? 


If you're running apache2 just locally, here's two ways to fix it that I know

[LIST]
[*] add this to /etc/apache2/apache2.conf
```

ServerName localhost

```

[*] add localhost.localdomain to /etc/hosts as alias to 127.0.0.1. This one is discouraged.
[/LIST][/QUOTE]

Thank you.

Your instruction really help me.
I managed to solve the problem.
But I still wondering why the by default the apache2.conf doesn't have the ServerName line?

---

### Post by mlind on 2006-06-27
[QUOTE=sirhan]Thank you.

Your instruction really help me.
I managed to solve the problem.
But I still wondering why the by default the apache2.conf doesn't have the ServerName line?[/QUOTE]

I think it's detected normally okay, but when running on host which domain is not
fully qualified, you get the error, dunno. I guess this setting is normally defined
per VirtualHost (sites-enabled folder contains virtualhost configurations).

There must some pretty simple explanation for this, but I haven't ever arsed to rtfm :mrgreen:

---

