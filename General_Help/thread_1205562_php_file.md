---
title: "php file"
date: 2009-07-06
forum: General Help
---

### Post by babbar.ankit on 2009-07-06
I have installed the php5 and apache 2
I am opening :
[http://localhost/drupal-6.13/install.php](http://localhost/drupal-6.13/install.php)
but the webrowser say Open with or save the file 
Its not opening the file in browser

---

### Post by credobyte on 2009-07-06
```
sudo apt-get install apache2 php5 libapache2-mod-php5 && sudo /etc/init.d/apache2 restart

```Try again !

---

### Post by masux594 on 2009-07-06
Do you use MySql for the website?
If yes, try the command in [this post]("http://ubuntuforums.org/showpost.php?p=7520121&postcount=3").. 

P.s. Have u rebooted after installation?

Sysc, A

---

### Post by credobyte on 2009-07-06
> **masux594 said:**
> Do you use MySql for the website?
If yes, try the command in [this post]("http://ubuntuforums.org/showpost.php?p=7520121&postcount=3").. 
The problem is PHP, not MySQL ;)

> **masux594 said:**
> P.s. Have u rebooted after installation?
Why to reboot if you can restart Apache ( and MySQL too ) ?

---

### Post by masux594 on 2009-07-06
@credobyte_1
I know =| .. i ask this question because the command that i post before, install mysql too.. then, if he doesen't use it, i have posted a the command without that =P

@credobyte_2
For the second question you're right.. i told that because in another post, someone tells that with rebooting [doesen't work restarting only apache] everythings work fine..

@babbar.ankit
In another post a user had the same problem and running this command ```
sudo a2enmod php5
``` all seems to work!

Sysc, A

---

### Post by babbar.ankit on 2009-07-06
It isn't wrkng sum1 hlp out

---

### Post by masux594 on 2009-07-06
Precisely [this post]("http://ubuntuforums.org/showpost.php?p=7545325&postcount=14")

Sysc, A

---

### Post by credobyte on 2009-07-06
> **babbar.ankit said:**
> It isn't wrkng sum1 hlp out

At least post the output of your executed commands ( previous posts ). There's no such a problem - "it's not working" ;)

---

