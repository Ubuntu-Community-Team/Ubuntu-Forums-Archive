---
title: "How can i hide folder on ubuntu /var/www directory"
date: 2012-05-29
forum: General Help
---

### Post by sumendra on 2012-05-29
Hi ,
 I am trying to host ajaxplore a web based FTP solution hosting under /var/www directory with www:data permission on my ubuntu server 10.04 LTS but as part of the security i need to hide some of the folder under /var/www/ajaxplorer/data to make it hidden form web user to view those directory with the direct URL. But i'm not able to hide those folder. Renaming the folder with . with the directory really won't work for me Please help me out to hide those folder form the web access .:(

---

### Post by zombifier25 on 2012-05-29
You can change its permission to 700. That way other people will get a 403 when they try to reach it.

---

### Post by sumendra on 2012-05-30
i tried with the file permission but it really not worth as the directory is under www:data user and its not worth by just changing the file permission . It is easily accessible even thought

---

### Post by marrok1 on 2012-05-30
can you give more details as to what you are trying to accomplish? have you tried making it hidden?

---

### Post by SeijiSensei on 2012-05-30
You can keep people from browsing directories with the -Indexes option in the virtual host definition:

```

<VirtualHost *:80>
[stuff]
<Directory /var/www/private>
    Options -Indexes
</Directory>
[stuff]
</VirtualHost>

```

See this page about the [Options]("http://httpd.apache.org/docs/2.2/mod/core.html#options") directive and this more general discussion of [access controls]("http://httpd.apache.org/docs/2.2/howto/auth.html") in Apache.

---

