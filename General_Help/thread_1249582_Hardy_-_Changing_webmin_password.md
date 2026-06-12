---
title: "Hardy - Changing webmin password"
date: 2009-08-25
forum: General Help
---

### Post by shanep-server on 2009-08-25
I installed lamp an webmin. When I log into webmin [Https://localhost:10000/](Https://localhost:10000/) I get the webmin log in screen.
I tried to use -

User - root
Password - root password

User - Admin
Password - root password

Neither worked. So I wanted to try an change the password the way they say on Webmin site.

# How do I change my Webmin password if I can't login?

Included with the Webmin distribution is a program called changepass.pl to solve erecisely this problem. Assuming you have installed Webmin in /usr/libexec/webmin, you could change the password of the admin user to foo by running
/usr/libexec/webmin/changepass.pl /etc/webmin admin foo 

I don't know where webmin_1.480_all.deb was installed too. I can't find it in /usr/ folder. I didn't not install it custom or anything just ran the .deb package. Does anyone know where it may have been installed too? Or does anyone know what I do to log into webmin for the first time?

Thank you for any suggestions

---

