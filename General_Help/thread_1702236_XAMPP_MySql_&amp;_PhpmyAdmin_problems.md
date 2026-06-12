---
title: "XAMPP MySql &amp; PhpmyAdmin problems"
date: 2011-03-07
forum: General Help
---

### Post by Coastalguy on 2011-03-07
I have had a LAMP (Sokkit), set up on my windows for years where I test websites before uploading. Now, dual booting between my XP and Ubunu Meerkat, I want first a backup if my xp fails, and also someday move over to Linux.

To accomplish this, I installed XAMPP for Linux. First, after having to do special mounting of my NTFS windows partition and changing the DocumentRoot and Directory for Apache2. I am now able to display my sites along with PHP code.

I now have 2 problems, relating to my MySql databases and PhpMyAdmin. First, on every database display on my sites, that run fine under Sokkit, I am getting the error: Warning: mysql_num_rows() expects parameter 1 to be resource, boolean given in /media/Sokkit/_LC/index.php on line 103. When I added a num_rows to display the number of records selected, it shows 0 records, although there are many records in the database, again which display fine on my windows Sokkit LAMP.

My second problem, is with PHPMyAdmin, which I can login and which displays databases from what I assume to be those installed into whatever default folder that was used? What I would like to do is repoint phpmyadmin to my existing databases on a different folder.

My localhost, which is working fine is: /media/Sokkit/
My Mysql databases are located under this localhose folder at: /media/Sokkit/Sokkit/mysql4/data

Can someone possibly help?
thanks, :cry:

---

