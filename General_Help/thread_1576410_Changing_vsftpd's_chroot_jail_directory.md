---
title: "Changing vsftpd's chroot jail directory"
date: 2010-09-17
forum: General Help
---

### Post by parsa28 on 2010-09-17
Hey there, I'm on LTS 10.04.1 and have a fresh copy of vsftpd installed. How do I change the chroot jail path for a single user to something other than it's home ? I want my front-end designer to have access to /var/www.

Cheers
Parsa

---

### Post by JedMeister on 2010-11-03
Not sure if you still need this answered of not, whether you solved it, or moved on to something else. I came across this in my travels and thought I'd chuck in my 2c, hope its useful.

How about attack this from a slightly different angle and make the user account a member of www-data group and assign /var/www as the users home? I reckon that should work. Just make sure that you set group permissions to read/write(/execute?) so the webserver won't be hindered from going about its business.

---

