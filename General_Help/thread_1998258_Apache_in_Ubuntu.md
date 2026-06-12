---
title: "Apache in Ubuntu"
date: 2012-06-06
forum: General Help
---

### Post by 1Yeoj1 on 2012-06-06
I recently installed LAMP (Linux Apache MySQL PHP, Perl and Python) on my Ubuntu flash drive,** not server **, and I could travel on localhost running It Works in Firefox. I then proceeded to produce a folder for a website I want to test on localhost. After that I have been getting error messages on the apache2 package. ```
joey@JoeyJump:~$ apache2 -k restartapache2: bad user name ${APACHE_RUN_USER}
```I was wondering if I could get some help?

Yeoj

---

### Post by alanphil on 2012-06-07
I would recommend XAMPP project:
[http://www.apachefriends.org/en/xampp.html](http://www.apachefriends.org/en/xampp.html)

This is a great way to experiment with LAMP server. You are probably running into issues because you are attempting to run LAMP server off of a flash drive.

---

### Post by lisati on 2012-06-07
> **1Yeoj1 said:**
> I recently installed LAMP (Linux Apache MySQL PHP, Perl and Python) on my Ubuntu flash drive,** not server **, and I could travel on localhost running It Works in Firefox. I then proceeded to produce a folder for a website I want to test on localhost. After that I have been getting error messages on the apache2 package. ```
joey@JoeyJump:~$ apache2 -k restartapache2: bad user name ${APACHE_RUN_USER}
```I was wondering if I could get some help?

Yeoj

I generally use this when I want to restart apache2:
```
sudo service apache2 restart
```

---

### Post by 1Yeoj1 on 2012-07-02
My problem was permissions and I changed them to 775 and I can do PHP, HTML ... the whole bit. Thank you for your help.

Yeoj

---

