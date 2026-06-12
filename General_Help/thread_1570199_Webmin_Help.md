---
title: "Webmin Help"
date: 2010-09-07
forum: General Help
---

### Post by zurek22 on 2010-09-07
alright so my apache files are compleatly new, just installed, i placed my server name in http.d file, but now i want webmin to create a VH and i cant figure out how to do it, i keep getting an error like

```
administrator@ServerHome:~$ sudo /etc/init.d/apache2 restart
 * Restarting web server apache2                                                                        
[Mon Sep 06 22:41:53 2010] [warn] NameVirtualHost *:80 has no VirtualHosts
 ... waiting [Mon Sep 06 22:41:54 2010] [warn] NameVirtualHost *:80 has no VirtualHosts
```

i dont know what is going on here

can you please explain clear im kinda a noob on this

---

### Post by CharlesA on 2010-09-07
What does httpd.conf look like?

This is what mine looks like with 2 virtualhosts:

```
<VirtualHost *:80>
ServerName atlantis
ServerAlias atlantis *.atlantis
DocumentRoot /var/www/atlantis
</VirtualHost>

<VirtualHost *:80>
ServerName music
DocumentRoot /var/www/music
</VirtualHost>
```

---

### Post by zurek22 on 2010-09-08
> **CharlesA said:**
> What does httpd.conf look like?

This is what mine looks like with 2 virtualhosts:

```
<VirtualHost *:80>
ServerName atlantis
ServerAlias atlantis *.atlantis
DocumentRoot /var/www/atlantis
</VirtualHost>

<VirtualHost *:80>
ServerName music
DocumentRoot /var/www/music
</VirtualHost>
```



well theres not much in there all it says is ServerName ServerHome

im attaching the file of my apache folder if u could can u help me

---

### Post by zurek22 on 2010-09-12
all fixed, i figured it out, and webmin helped me, had a big problem with the ports file and the http.d you have to configure them both to view the page, so yea i fixed it thanks for every ones help

---

