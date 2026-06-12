---
title: "shared dir permission problem"
date: 2009-11-06
forum: General Help
---

### Post by rslaqui on 2009-11-06
Hi I'me a newbie trying to do things with out the insecure 777 permission


I want to allow different users to write on 

/var/www

So I created a group: web
and chowned /var/www so it belonged to root:web (it was root:root)
and made permissions 770

Then I added webdeveloper1 to the group web and verified at the groups file that it was in fact part of the group.

Finaly I tried to copy a file from webdeveloper1 home to /var/www

but the permissions is denied

- tried setting the stiky bit (as far as I understood this is not the problem but I tried it any way) same result.

- tried using another dir (in case var was protected) - same result

- tried on an older ububtu -same result (my system is 9.10 x64 tried in a 8.?? x86)


What I'm doing/understanding wrong?

Thanks a lot

---

### Post by hal10000 on 2009-11-06
I think it's no good idea ti change the owner or the permissions of the webservers document root  (/var/www) (i guess it's apache2 ??) This might lead to security risks

It's better to create a subdirectory inside /var/www
```
sudo mkdir /var/www/webdevelopers
sudo chown -R :web /var/www/webdevelopers
sudo chmod 0775 /var/www/webdevelopers

```
and tell your developers to create their files inside this directory

Another - and presumably the best - solution may be to create **per user webdirectories** and follow this documentation:
[http://httpd.apache.org/docs/2.2/howto/public_html.html](http://httpd.apache.org/docs/2.2/howto/public_html.html)

---

### Post by pjbgravely on 2009-11-06
The above post has a better solution.

Make sure you are copying as the user webdeveloper1 and not another user by using whoami in the terminal.

Paul

---

### Post by rslaqui on 2009-11-07
Thanks a lot with the -R command it works on a /var/www/webdevelopers/ ----- but just to learn ¿why it doesn't work on /var/www?

Is there an other layer/system/way of permissions that overrides chmod?
becaused ls -la in /var and /var/www throws

...
drwxrwsr-x  3 root web  4096 2009-11-07 10:14 www
..
-----------------------------------------------------------------------------------------------
..
drwxrwsr-x  2 root web  4096 2009-11-07 10:19 webdevelopers
...

thanks once more

---

