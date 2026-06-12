---
title: "installing php"
date: 2010-05-26
forum: General Help
---

### Post by Existance0 on 2010-05-26
Well, I went to install the PHP module for apache just now and it appears some of the files are missing?
```
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/p/php5/php5-common_5.3.2-1ubuntu4.1_i386.deb 404  Not Found [IP: 91.189.88.45 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/p/php5/libapache2-mod-php5_5.3.2-1ubuntu4.1_i386.deb 404  Not Found [IP: 91.189.88.45 80]
```

---

### Post by bodhi.zazen on 2010-05-26
Try :

```
sudo apt-get update && sudo apt-get install php5
```

---

### Post by Existance0 on 2010-05-26
Thanks, it installed but it appears apache doesn't have the module loaded. Where does the package install libphp5.so? I tried locating it but came up with nothing.

---

### Post by sylvester_0 on 2010-05-26
If you're using a stock install of apache2 it's enabled by default. I don't know if installing php5 triggers reloading apache - have you tried that?

---

### Post by bodhi.zazen on 2010-05-26
> **Existance0 said:**
> Thanks, it installed but it appears apache doesn't have the module loaded. Where does the package install libphp5.so? I tried locating it but came up with nothing.

Install libapache2-mod-php5

Then 

```
sudo a2enmod php5
sudo service apache2 restart
```

Clear your browsers cache and try again.

---

### Post by WorMzy on 2010-05-26
Make sure that libapache2-mod-php5 is installed.

---

### Post by Existance0 on 2010-05-26
This actually wasn't the problem tbh I don't know what the problem was I did a bunch of stuff which didn't help and then I added an AddType to the .htaccess file and it fixed it. But strangely deleting it everything remained fixed. Thanks for all your help everyone. ^^

---

