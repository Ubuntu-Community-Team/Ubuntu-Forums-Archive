---
title: "Perl problems with Apache2 server"
date: 2006-05-27
forum: General Help
---

### Post by Herbal on 2006-05-27
Ok, so I recently switched over to linux and am picking up on it fast. I have installed Apache, the mods for perl to work with apache and yet when I try to access the perl files on my server it, it asks how I would like to open the file instead of veiwing as a web page. Any Ideas?

---

### Post by adamkane on 2006-05-27
You have to start off with a good install:

Apache2/PHP4/MySQL4 (breezy or dapper):
```

sudo apt-get install apache2 php4 mysql-client mysql-server phpmyadmin libapache2-mod-php4 libapache2-mod-auth-mysql php4-mysql

```

Apache2/PHP5/MySQL4 (breezy or dapper):
```

sudo apt-get install apache2 php5 mysql-client mysql-server phpmyadmin libapache2-mod-php5 libapache2-mod-auth-mysql php5-mysql

```

Apache2/PHP5/MySQL5 (dapper):
```

sudo apt-get install apache2 php5 mysql-client-5.0 mysql-server-5.0 phpmyadmin libapache2-mod-php5 libapache2-mod-auth-mysql php5-mysql

```

---

### Post by Herbal on 2006-05-27
Good install but still no change.

---

### Post by adamkane on 2006-05-27
What have you done to enable perl support? Can you post info about the perl scripts you're trying to run?

---

### Post by Herbal on 2006-05-27
I am just running a bisic perl script. Here is the code

#!/usr/bin/perl 
print ("Hello World");

Thats all thats in the file.
Other than that I have gone through synaptic and downloaded the mods that integrate apache and perl. Do I need to mod the httpd.conf file?

---

### Post by Herbal on 2006-05-27
I just reinstalled the libapache-mod-perl and still no go. I am thoroughly stumped.

---

### Post by adamkane on 2006-05-27
Uninstall that, and install libapache2-mod-perl2.

---

### Post by Herbal on 2006-05-27
Done, except it still refers to the .pl file as one I have to download to open instead of viewing as a page.](*,)

---

### Post by adamkane on 2006-05-27
Can you post a .pl example, that I can test. 

Do you have the files, that I posted in Post 2 installed?

---

### Post by Herbal on 2006-05-27
Yes, I installed the files from the second post. I am trying to access a file called perl.pl with the following code in it.

#!/usr/bin/perl
print ("Hello World");

This should display a page with the text "hello world" correct?

---

### Post by MichaelD on 2006-06-01
Have you enabled Perl support in your httpd.conf?

example:

AddHandler cgi-script .cgi
AddHandler cgi-script .pl

---

