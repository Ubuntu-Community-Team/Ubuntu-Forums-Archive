---
title: "How can I check if I have correctly installed the LAMP server"
date: 2011-10-14
forum: General Help
---

### Post by beginer123 on 2011-10-14
I am two days ago, first installed Ubuntu 10.04
 Yesterday I made the upgrade to version 11.10
 I installed Apache2, MySQL, PHP5 and (LAMP??)
 I was able to access localhost, MySQL and phpMyAdmin
 How can I check if I have correctly installed the LAMP server?
 What should I start?
 I do not know anything about Linux Ubuntu, I'm a total beginner to Ubuntu.
 (On Windows I have worked with XAMPP, is it similar?)
 I want to install phpBB3 and Joomla and I'm not sure if I have correctly installed the LAMP.

---

### Post by Ctrl+Alt+Del on 2011-10-14
if you can access phpmyadmin it works :)
Since phpmyadmin requires a working webserver and php + mysqlserver it should be proof enough :)

you can now add your webstuff to /var/www or to a folder called public_html in your home directory if you enable mod_userdir for apache.

mysql can be accessed via "mysql -u root -p" from cli

---

### Post by beginer123 on 2011-10-14
> **Ctrl+Alt+Del said:**
> if you can access phpmyadmin it worksThank you for your response
 I can now access in MySQL, I have the correct access to localhost "It Works"
 I can access the phpMyAdmin panel and I created a new SQL database.
 So, these three steps are confirmation that I have correctly installed the LAMP :)

 I have another question.

 Do I have to first make a phpBB3 download from the Internet and unzip the downloaded file, or may be directly from the terminal to install phpBB3?

 Thanks

---

### Post by Ctrl+Alt+Del on 2011-10-14
Well it kind of depends on your needs, the ubuntu prepackaged version will do fine if you don't plan on modding it to heavily. 
Basically you get easy upgrades and a solid preconfigured security setup by sacrificing the ability for heavy customization. A downloaded version is a tad more complicated to set up and you will be required to upgrade it by hand whenever new releases are out. On the plus side; since you are the one doing the upgrade you can prevent your customizations from breaking.

It really depends on your requirement, a minimal forum for the average tennisclub is better done trough apt, a heavily used forum with lots of custom tuning is better done from scratch...

---

### Post by beginer123 on 2011-10-14
> **Ctrl+Alt+Del said:**
>  A downloaded version is a tad more complicated to set up and you will be required to upgrade it by hand whenever new releases are out. Thanks for Your answer.

---

