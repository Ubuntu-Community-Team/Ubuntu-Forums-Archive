---
title: "Making user able to access folder via group"
date: 2011-06-27
forum: General Help
---

### Post by pqwoerituytrueiwoq on 2011-06-27
```
cat /etc/group | grep www-data | grep chad
chad:x:1000:www-data
```
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=196131&stc=1&d=1309216968[/IMG]
the user www-data should have read access to my folder but i am still getting a 403 forbidden error
i have done this before without issue anyone see what is wrong?
i have a folder i use for file transfers over IM it is more reliable than the messengers file transfer abilities

---

### Post by doas777 on 2011-06-27
so to clarify, you want the user www-data (your webserver) to access your folder within your home (and serve up a page), using owner group permissions to do so? is that correct?

if that is the case, you need to make your webserver the ownergroup for your folder.
```

sudo chown chad:www-data

```
you may want to consider setGid so that all files created in the folder will take on the groupowner on the folder. it will also make all files within the folder execute as www-data.

---

### Post by pqwoerituytrueiwoq on 2011-06-27
```
chad@lucid-desktop:~$ sudo chown chad:www-data /home/chad/
chad@lucid-desktop:~$ sudo chown chad:www-data /home/chad
chad@lucid-desktop:~$ sudo chown chad:www-data /home/chad/Desktop/
chad@lucid-desktop:~$ sudo chown chad:www-data /home/chad/Desktop
```still forbidden
here is part of my */etc/apache2/sites-available/default* file
```
<VirtualHost *:81>
    DocumentRoot /home/chad/Desktop
    <Directory /home/chad/Desktop/>
        Options FollowSymLinks
        AllowOverride All
        Order allow,deny
        allow from all
    </Directory>
</VirtualHost>
```

---

### Post by doas777 on 2011-06-27
well, doing that to your entire home is not recommended. I would really pick a single subfolder to modify.

I'm really not sure what you are trying to do, so I can only advise you to check your logs for hints as to why its not working.
good luck.

---

### Post by pqwoerituytrueiwoq on 2011-06-27
since the user www-data is in the group chad and the group has read access to the folder www-data should be able to read the files in it but for some reason it can't

---

### Post by pqwoerituytrueiwoq on 2011-06-27
seems it doe have access but no permission to list all files:lolflag: now to fix that (and figure out how) off to google i go
solution
```
<VirtualHost *:81>
        DocumentRoot /home/chad/Desktop
        <Directory /home/chad/Desktop/>
                Options FollowSymLinks
               ** Options +Indexes**
                AllowOverride All
                Order allow,deny
                allow from all
        </Directory>
</VirtualHost>
```

---

