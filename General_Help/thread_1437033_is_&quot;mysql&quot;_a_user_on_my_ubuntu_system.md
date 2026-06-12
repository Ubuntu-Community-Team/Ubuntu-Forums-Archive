---
title: "is &quot;mysql&quot; a user on my ubuntu system?"
date: 2010-03-23
forum: General Help
---

### Post by zensys on 2010-03-23
perhaps a newbie question or for the mysql forum but I'll give it try here:

I use 9.10 desktop with a root user and my own user (timmo), I did not create anything else. Now I check a directory (mysql databases) with ls -l and I see mysql not only as a group but also as owner. How can mysql, not being a user on my system, be an owner? In users and groups I see that all of the many groups only have two members, root and timmo.

I know that mysql users and linux users are different animals but ls -l is definitely a linux command.

thanks for helping me out.

---

### Post by cjhabs on 2010-03-23
> **zensys said:**
> perhaps a newbie question or for the mysql forum but I'll give it try here:

I use 9.10 desktop with a root user and my own user (timmo), I did not create anything else. Now I check a directory (mysql databases) with ls -l and I see mysql not only as a group but also as owner. How can mysql, not being a user on my system, be an owner? In users and groups I see that all of the many groups only have two members, root and timmo.

I know that mysql users and linux users are different animals but ls -l is definitely a linux command.

thanks for helping me out.

A list of all the users on the system can be found with:
cat /etc/passwd

A list of all the groups on the system can be found with:
cat /etc/group

To check specifically for the mysql user, you can do:
grep mysql /etc/passwd

---

### Post by pcjunkie on 2010-03-23
MySQL is owned by root, the whole web server is. When you change permissions do it through group policy not file policy and only do it on specific folders like the webserver public_html 

As posted above that will change the password and reveal the user groups.

You can check groups on the folder properties menu as well. Keep it as root to ensure security and don't add your user account to that group as this can cause headaches.

---

