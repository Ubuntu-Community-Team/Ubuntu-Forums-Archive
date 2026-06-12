---
title: "Ubuntu 9.10 - phpmyadmin login problems!"
date: 2009-11-02
forum: General Help
---

### Post by J2099 on 2009-11-02
Hi guys...
I have recently installed Ubuntu 9.10, and I have installed LAMP aswell. Apache, MySQL & PHP look like they are worling fine. However, I have installed phpmyadmin and It does not seem to be letting me login. I've uninstalled and reinstalled it a few times, and I'm still having no luck.

I remember on Ubuntu 9.04, if you did not enter a password for phpmyadmin then your password would be "password". I tried this and it did not work, I also tried leaving the password field blank too.

I'm all out of ideas.
Does anyone know the solution?
And has anyone else had this problem?


Thanks


Jason

---

### Post by shakty on 2009-11-11
I have the same problem and I am quite puzzled....

---

### Post by J2099 on 2009-11-11
I've actually gone back to using 9.04, because 9.10 was giving me too many other problems. For example, I uninstalled LAMP which lead to alot of other files being removed and then when I restarted my PC I was unable to access the Ubuntu GUI. Karmic Koala needs a bit more fine-tuning IMO.

However, I'm sure I sorted this MySQL problem out before I went back to using Ubuntu 9.04. If I remember correctly, I uninstalled MySQL then I reinstalled it. I think the problem was that I never put a password for the mysql, so I made sure I entered my own password.


Hope that helps.;)

---

### Post by shakty on 2009-11-11
I would prefer not reinstall MYSQL, anyway thanks for the hint! I will work on that!

---

### Post by shakty on 2009-11-11
SOLVED.

I used the config.sample.inc.php as the new config.inc.php
I edited it setting:

$cfg['Servers'][$i]['auth_type'] = 'HTTP';

It means that I can login with any valid mysql user which has a password. 

I created a new username with a valid password with the command

CREATE USER 'user' IDENTIFIED BY 'password';

And then I could login!!! :D

Other useful commands that could help in such cases are:

--


UPDATE mysql.user SET Password=PASSWORD('MyNewPass') WHERE User='root';
FLUSH PRIVILEGES;
--
GRANT ALL ON dbname.tablename TO 'user'; -- * as wild card

--
GRANT SELECT,INSERT,UPDATE,DELETE ON *.* TO 'user';

---

