---
title: "/usr/sbin/setsebool: No such file or directory"
date: 2011-11-12
forum: General Help
---

### Post by afrodeity on 2011-11-12
I have installed wordpress on localhost and need to change the way it connects, as per this tutorial:

[http://www.nerdgrind.com/wordpress-automatic-upgrade-plugin-failed-or-not-working/](http://www.nerdgrind.com/wordpress-automatic-upgrade-plugin-failed-or-not-working/)

If I try:

```

/usr/sbin/setsebool -P httpd_can_network_connect=1
```

I get 

```

/usr/sbin/setsebool: No such file or directory

```

I've tried adding sbin to my path.

a locate for setsebool turns up nothing, as does apt-cache search.

Please help:confused:

---

### Post by Lars Noodén on 2011-11-12
It should be in the package [policycoreutils ](http://packages.ubuntu.com/search?searchon=contents&keywords=setsebool&mode=exactfilename&suite=oneiric&arch=any).  Do you have that installed yet?

---

### Post by hwttdz on 2011-11-12
"sudo apt-get install policycoreutils" should get you setsebool.

---

### Post by afrodeity on 2011-11-12
Thanks, I didn't realise it was an SElinux problem. I guess I have to set my permissions for my wordpress installation back to what they were. 

I think I did this before I got to the above SElinux solution:

```

chmod -c 777 -R /usr/share/wordpress/

```

Which is probably wrong, since I'm still stuck with wordpress asking for ftp information.

UPDATE: It was an ownership problem. This worked:

```

sudo chown -R www-data:www-data 

```

Do it to your wordpress folder, eg, /usr/share/wordpress.

The folder needs to be owned by the webserver. I added a wildcard *

---

