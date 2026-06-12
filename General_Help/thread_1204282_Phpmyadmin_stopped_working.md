---
title: "Phpmyadmin stopped working?"
date: 2009-07-04
forum: General Help
---

### Post by K34nu on 2009-07-04
Hello,

I installed phpmyadmin yesterday, and well.. It was working fine yesterday, could access everything fine.. And I went on today and im getting the following error:

```



Welcome to phpMyAdmin 2.11.8.1deb1

phpMyAdmin tried to connect to the MySQL server, and the server rejected the connection. You should check the host, username and password in your configuration and make sure that they correspond to the information given by the administrator of the MySQL server.

Error
MySQL said:  

#1045 - Access denied for user 'root'@'localhost' (using password: NO) 

 
Invalid hostname for server 1. Please review your configuration. 

```

Does anyone have any idea at all? I do have a password for root, but I can't enter it?.. Nor would I know where to enter it?.. 

Can anyone help?

Thanks
-Keanu

---

### Post by LoneWolfJack on 2009-07-04
open a console window and type

```
mysql -uroot -p<yourpass>
```

and post the output

---

### Post by K34nu on 2009-07-04
```

root@ARO-IRL:/opt/mangos/bin# mysql -u root -p
Enter password:
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 179
Server version: 5.0.67-0ubuntu6 (Ubuntu)

Type 'help;' or '\h' for help. Type '\c' to clear the buffer.

mysql>

```

-Keanu

---

### Post by LoneWolfJack on 2009-07-04
> Invalid hostname for server 1. Please review your configuration.

ok, I overlooked that.
check your phpmyadmin config. there probably is a wrong ip address in the config of server 1.

---

### Post by K34nu on 2009-07-04
How would I go around checking my phpmyadmin config?

Thanks
-Keanu

---

### Post by wojox on 2009-07-04
Look here in terminal 

```
gksudo gedit /etc/apache2/apache2.conf
```

Then look for this line

Include /etc/phpmyadmin/apache.conf

If not there put it there.

Then restart apache

```
sudo /etc/init.d/apache2 restart
```

Then surf on over to

[http://domain/phpmyadmin](http://domain/phpmyadmin)

---

### Post by K34nu on 2009-07-04
I'm still getting the same error for some reason?... I have no idea why..

I personally think that the phpmyadmin may have the wrong config or something? I don't know... Is there a script like phpmyadmin? Or something? Or a way to get this working?

Thanks.

-Keanu

---

### Post by vikkikanhaua on 2009-07-04
I'think you are not entering the password in phpmyadmin coz it's showing 'using password: NO'. if that's correct then enter the password & try again

---

### Post by K34nu on 2009-07-04
Thats my point, I don't get a chance to enter the password. It just directly goes to the page thats showing?.. 

Thanks
-Keanu

---

### Post by vikkikanhaua on 2009-07-04
can you post a screenshot of phpmyadmin login page

---

### Post by wojox on 2009-07-04
All right try

```
gksudo gedit /etc/phpmyadmin/apache.conf
```

Look for

/* Authentication type and info */
$cfg['Servers'][$i]['auth_type'] = 'config';
$cfg['Servers'][$i]['user'] = 'root';
$cfg['Servers'][$i]['password'] = '123456789';
$cfg['Servers'][$i]['AllowNoPasswordRoot'] = true;

Make sure they match up.

```
sudo /etc/init.d/mysql restart
```

```
sudo /etc/init.d/apache2 restart
```

---

### Post by K34nu on 2009-07-05
Uhm, Sorry for the late reply. I checked in the apache.conf file with "nano" and well, I didn't find anything saying anything of the following:

```

/* Authentication type and info */
$cfg['Servers'][$i]['auth_type'] = 'config';
$cfg['Servers'][$i]['user'] = 'root';
$cfg['Servers'][$i]['password'] = '123456789';
$cfg['Servers'][$i]['AllowNoPasswordRoot'] = true;

```

Absolutly nothing at all saying that. Any ideas?

The main thing that concerns me is the fact that it worked before? And now it has stopped working..

Thanks
-Keanu

---

### Post by K34nu on 2009-07-06
bump?... Sorry but I need to get this fixed...

-Keanu

---

### Post by zemon_ on 2009-07-18
K34nu did you manage to fix this?

Im also getting the same error

---

### Post by zemon_ on 2009-07-18
I fixed it by doing this.

Edit /var/lib/phpmyadmin/config.inc.php;

Change the option value 'config' to 'cookie'.

Edit this line 

$cfg['Servers'][$i]['host']=''; phpinfo();//'] = 'localhost'; 

To this 

$cfg['Servers'][$i]['host']= 'localhost';

---

### Post by sredlich on 2010-07-26
> Invalid hostname for server 1. Please review your configuration.

I fixed this on my server.

$ sudo dpkg-reconfigure phpmyadmin

and selecting yes for configuring DB.

---

