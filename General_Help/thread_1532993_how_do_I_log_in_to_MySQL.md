---
title: "how do I log in to MySQL?"
date: 2010-07-17
forum: General Help
---

### Post by engine on 2010-07-17
Clean installation of 10.04 after a hard disk crash ... so long since the last new install there are some things I've completely forgotten how to do.

One question per post, so the question in this one is "How do I log in to MySQL?" One forum contributor says
> When installing MySQL I believe it prompts you to set a password for the root account.
If only <g> (and it should, damnit!)

I've tried logging in with my own user-id and my default password, my own user-id and no password, 'root' as user-id and my default password, 'root' as user-id and no password: all with equal lack of success.

```
{my user id}@nb:~$ mysql -u {my user id}
ERROR 1045 (28000): Access denied for user '{my user id}'@'localhost' (using password: NO)
{my user id}@nb:~$ mysql -p
Enter password: 
ERROR 1045 (28000): Access denied for user '{my user id}'@'localhost' (using password: YES)
{my user id}@nb:~$ mysql -u root
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: NO)
{my user id}@nb:~$ mysql -u root -p
Enter password: 
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: YES)
{my user id}@nb:~$ 
```

What do I try next?

---

### Post by wojox on 2010-07-17
It always asks for a root password. Try [MysqlPasswordReset]("https://help.ubuntu.com/community/MysqlPasswordReset")

---

### Post by engine on 2010-07-23
Thanks for the tip, but it didn't get me anywhere :-{

Uninstall next, then try a re-install just to make sure I have skipped any friendly SET ROOT PASSWORD prompts ... I mean, if that's part of installation then surely a well-maintained installer will include it?

---

### Post by Bertus_Nel on 2010-07-23
Hi

Did you perhaps try # sudo bash (Enter) - then /etc/init.d/mysql reset-password then you should get something in this effect:

New MySQL root password:
Verify:
Setting new MySQL root password

---

### Post by engine on 2010-10-10
Tried that too, and still no luck ... perhaps the tip "use the service utility" doesn't actually mean "enter service mysql reset-password at the shell prompt". Farther advice still welcome!

> root@MyBox:~# /etc/init.d/mysql reset-password
Rather than invoking init scripts through /etc/init.d, use the service(8) utility, e.g. service mysql reset-password

The script you are attempting to invoke has been converted to an Upstart job, but reset-password is not supported for Upstart jobs.

root@MyBox:~# service mysql reset-password
Rather than invoking init scripts through /etc/init.d, use the service(8) utility, e.g. service mysql reset-password

The script you are attempting to invoke has been converted to an Upstart job, but reset-password is not supported for Upstart jobs.
root@MyBox:~# 

---

### Post by engine on 2010-11-04
[bounce] Isn't there *anyone* out there who knows how I can run the reset-password command for MySQL?

---

