---
title: "enable Mod Rewite on apache2?"
date: 2006-02-25
forum: General Help
---

### Post by spahn on 2006-02-25
i have apache2 installed on my development machine (installed via the package manager) and it will not allow me to use mod-rewrite! looks like the mod is not enabled. Any ideas on how to enable it???
i tried sim-linking the mods-available to the mods enabled (like the way that you do name-based virtual domains in apache2) but that didn't work...:-k

---

### Post by az on 2006-02-25
sudo a2enmod rewrite

---

### Post by spahn on 2006-02-26
Thank you soo much, i thought that it was MUCH more difficult....
Thank you!

---

### Post by Burgresso on 2006-08-03
azz

thanks for your post - awesome - my termal responded

> 
[FONT="Courier New"]This module is already enabled![/FONT]


But still apache does not user/find/enable it, even after restarting. Any ideas?

gracias

burgresso

---

### Post by spahn on 2006-08-04
Look into your log files (ie. /etc/logs/apache/error.log)

---

### Post by TOM1 on 2006-08-29
I have the same problem. :???: 

When I typed a2enmod rewrite my computer says:
This module is already enabled!

Still I get Internal server error after I try add some rewrite rules to my .htaccess file.

Error log gives:
[Tue Aug 29 20:51:51 2006] [alert] [client 10.0.0.5] /home/ma/public_html/.htaccess: Options not allowed here

---

### Post by spahn on 2006-08-29
You might have apache2 installed but not running as your primary- i had apache and apache2 installed on my development environment and it prefered not to use apache2. 
Have you recently upgraded?
that is all i can think of right now, (i am at work)
Good luck - when you figure it out, send me your reply or post it here.

---

