---
title: "upload on server"
date: 2011-05-23
forum: General Help
---

### Post by !! hack-back !! on 2011-05-23
hello guys
i have server 10.10
and i installed lamp server and ftp server
the first problem is when i upload file through ftp it have root permission so i cant view from browser it says forbidden then when i change it to 755 it open but every file i upload it i must chmod it ...

the second problem that when i use any php file for uploading it didnt upload any thing ...
please i need help for important 

:(

---

### Post by !! hack-back !! on 2011-05-24
no answer ...... 
still waiting ........

---

### Post by rbishop on 2011-05-24
I am guessing there is a size limit on the page you are using.  Let's see the code you are using for that page.

---

### Post by webofunni on 2011-05-24
> **!! hack-back !! said:**
> hello guys
i have server 10.10
and i installed lamp server and ftp server
the first problem is when i upload file through ftp it have root permission so i cant view from browser it says forbidden then when i change it to 755 it open but every file i upload it i must chmod it ...

the second problem that when i use any php file for uploading it didnt upload any thing ...
please i need help for important 

:(

Which FTP server you are using ? and which php upload script you are using ?

Can you try [http://php.about.com/od/advancedphp/ss/php_file_upload.htm](http://php.about.com/od/advancedphp/ss/php_file_upload.htm) and let us know the result.

---

### Post by !! hack-back !! on 2011-05-24
it give me Sorry, there was a problem uploading your file.

---

### Post by !! hack-back !! on 2011-05-24
and am sure that the problem isn't from the php upload file because i try more than one script so the server need some thing !

---

### Post by webofunni on 2011-05-24
check the error log. paste the content here. 

```

tail -50 /var/log/apache2/error.log

```

Make sure that the location to which you are uploading the file has write permission for apache. 

Say, you are uploading the file to /var/www/upload then do

```

sudo chown www-data:www-data /var/www/upload

```

---

