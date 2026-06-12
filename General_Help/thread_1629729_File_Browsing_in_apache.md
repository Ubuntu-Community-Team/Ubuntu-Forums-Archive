---
title: "File Browsing in apache"
date: 2010-11-24
forum: General Help
---

### Post by Carlos67 on 2010-11-24
You don't have permission to access / on this server.
 
I changed the Documentrootvariable in /etc/apache2/sites-enabled/000-default
```
 
           # DocumentRoot /var/www
              DocumentRoot /home/***/svn/webDatabase/31
 

``` 
 
I changed the directory tag in /etc/apache2/sites-enabled/000-default
```
 
        # <Directory /var/www/>
        #       Options Indexes FollowSymLinks MultiViews
        #       AllowOverride None
        #       Order allow,deny
        #       allow from all
        # </Directory>
 
        <Directory /home/***/svn/webDatabase/31/>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride None
                Order allow,deny
                allow from all
        </Directory>
 

```
 
I changed folder acces and restarted the apache server
 
```
 
sudo chmod 777 /home/***/svn/webDatabase/31
sudo /etc/init.d/apache2 restart

```
 
While typing this I realised the syntax of the chmod was incorrect and i forgot the last /
 
```

sudo chmod 777 /home/***/svn/webDatabase/31 <<< this is incorrect @$!@#$%
sudo chmod 777 /home/***/svn/webDatabase/31/

```
 
So now while writing this ,after hours of searching getting to a point of despair to actually ask for help on this forum, I answerd my own question.
 
I post this anyway because it might help somebody
 
Carlos

---

