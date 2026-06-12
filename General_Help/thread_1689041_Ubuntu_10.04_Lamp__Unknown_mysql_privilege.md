---
title: "Ubuntu 10.04 Lamp : Unknown mysql privilege"
date: 2011-02-16
forum: General Help
---

### Post by DeanLearner on 2011-02-16
Hi,

I recently created a server through VPS.net from their Ubuntu 10.04 LAMP image.

Under the MySQL privileges I have noticed a permission for 'root'@'ubuntu'

[IMG]http://chrismingay.co.uk/vps.net/vps_mysql.png[/IMG]

Is this a standard thing for Ubuntu, or have VPS.net added it to their image?

If the former, what is it for? And do I need to keep it?

Thanks
-Chris

---

### Post by Habitual on 2011-02-16
My guess without too much investigation is that this is from the installation (from the repo maybe)?
VPS.net doesn't specify on their webpage any "ubuntu" reference.

Again, just a guess.
I wouldn't touch it and if you do, a couple of things to do or try first...

```
sudo mysqldump mysql> mysql_dump.sql
```

and/or

Change the password for **THAT specific root**@ubuntu user.

---

