---
title: "problem with apache directory"
date: 2009-11-05
forum: General Help
---

### Post by Kamils2 on 2009-11-05
hi
I have small problem.
I install yesterday lamp.
Everything was all right but when I set new apache root directory (kevin/home/public_html/) i can't use server. When I open localhost via www i see "403 forbidden". 

I set new directory in "site-defaults".

I don't know why this error I have ;/ Everything work's ok mysql, phpmyadmin, but this directory is only error ;/ 

Please help me with this Kevin 

PS. Sorry for me english I don't use this language long time.

---

### Post by Azdour on 2009-11-05
Hi,

Is kevin/home/public_html/ owned by www-data? I believe Apache needs to own the directories and pages under public_html to access them.

---

### Post by Kamils2 on 2009-11-05
hmm i'm thnik no ... i try to change this but i don't know how i start googling about this :)

---

### Post by liquidbee on 2009-11-05
You shouldn't change the default Apache document directory. Instead, enable mod_userdir.

---

### Post by Wandel on 2009-11-05
> **Azdour said:**
> Hi,

Is kevin/home/public_html/ owned by www-data? I believe Apache needs to own the directories and pages under public_html to access them.Apache does not need to own the files and folders, but they do need to be able to be read by others.

---

### Post by Kamils2 on 2009-11-05
ok so I change in dir proporites -> permissions -> others -> file acccess : read and write & folder access: create and delete files 
but it's still don't change this error ;/ still on my localhost I see 403 Forbidden ... please kill me ;/ 

I install lamp on ubuntu four times since 2007 ... i install this on 7.10 , 8.04, 8.10 and 9.04 i have problems with mysql and phpmyadmin with change root directory never and now on 9.10 something like this ...

---

### Post by preonet on 2009-11-06
**PLEASE HELP!!!**



**Forbidden**

 You don't have permission to access / on this server.




This is everything I get at web-broswer screen when trying to get to my web-page. 



I've ordered web-redirect from dns provider to IP address of my Ubuntu 9.10 server. When I type IP in browser - everything ifs fine, but assoon as I use domain name - I get this Forbidden ...




And in apache lof files I can see ...Permission denied ....




PLEASE HELP !!!

---

### Post by Wandel on 2009-11-06
It's not some stupid little thing like you have .htaccess file in there messing things up for you?

Edit: Also, the error log is usually helpful. Unless you have changed anything, it's at /var/log/apache2/error.log

---

