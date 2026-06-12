---
title: "[HowTo] Login Without a Password"
date: 2010-01-09
forum: General Help
---

### Post by frt975 on 2010-01-09
[SIZE=3]Note: Only do this if you understand the consequences of this. It allows attackers to gain access to the account you're removing the password form. It kills kittens too.
[/SIZE] 
[LIST=1]
[*]The first step: removing the password: ```
sudo passwd -d *username*
```
[*]Tell GDM to to allow you to login without a password: ```
sudo -i
echo "PasswordRequired=false" >> /etc/gdm/gdm.conf
exit

```
[/LIST]
Source: [http://linuxdesk.wordpress.com/2008/06/16/how-do-i-login-ubuntu-desktop-user-without-a-password/](http://linuxdesk.wordpress.com/2008/06/16/how-do-i-login-ubuntu-desktop-user-without-a-password/)

---

