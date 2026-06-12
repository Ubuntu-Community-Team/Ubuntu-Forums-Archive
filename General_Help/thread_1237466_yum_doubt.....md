---
title: "yum doubt...."
date: 2009-08-11
forum: General Help
---

### Post by veda87 on 2009-08-11
i need to download files from my server and install it.... I came to know abt yum and rpm....

I tried to install by means of rpm ```
rpm -ivh ftp://192.168.0.254/pub/Server/* --force --nodeps
```

this worked perfectly.... 

Then I tried installing through yum.....It asked me to define a additional repositories... so I created a file named **server1.repo** in **/etc/yum.respos.d**```
[server1]
name = server1 Server
baseurl = ftp://192.168.0.254/pub/Server/
enabled = 1
gpgcheck = 0
```
after, cleaning up using```
yum clean all
``` I tried installing by ```
yum install dovecot
```
I got an error message like```
IoError: <urlopen error unknown url type: media>
```
I couldn't figure out my mistake... can anyone point it out....:confused:

---

