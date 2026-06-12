---
title: "Phpmyadmin access forbidden after setting up Drupal"
date: 2009-12-10
forum: General Help
---

### Post by alicemoon on 2009-12-10
I have been trying to set up Drupal on my computer and have installed mysql, apache2, drupal and phpmyadmin. After some initial problems I got 
phpmyadmin working but could not access Drupal - after following various threads I got access to drupal and set it up but then discovered that i could no longer get into phpmyadmin as I was getting the following message

You don't have permission to access /phpmyadmin on this server.

I checked that I had the following line
Include /etc/phpmyadmin/apache.conf

in the /etc/apache2/apache2.conf file

when I restart apache I get the following error and am not sure if it is significant
 [warn] The Alias directive in /etc/phpmyadmin/apache.conf at line 3 will probably never match because it overlaps an earlier Alias.
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
 ... waiting [Thu Dec 10 09:14:12 2009] [warn] The Alias directive in /etc/phpmyadmin/apache.conf at line 3 will probably never match because it overlaps an earlier Alias.
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName

---

### Post by autonomy on 2010-04-10
You don't need that line in your Apache configuration b/c Ubuntu "already copied the file phpmyadmin.conf into /etc/apache2/conf.d  directory."

---

### Post by alicemoon on 2010-04-12
thanks for the answer - I did manage to get back in after I made the original post - but it always helps to know what went wrong

---

