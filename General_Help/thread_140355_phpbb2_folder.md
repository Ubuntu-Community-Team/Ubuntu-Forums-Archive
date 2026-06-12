---
title: "phpbb2 folder?"
date: 2006-03-06
forum: General Help
---

### Post by joshchernoff on 2006-03-06
Where are the files for the phpbb templets at? I dont see anything in the /var/www folder.

---

### Post by drunkez on 2006-04-22
i can see it in /usr/share/phpbb2  do a symlink to var/www
and you go

---

### Post by Scorpuk on 2006-05-27
[QUOTE=drunkez]i can see it in /usr/share/phpbb2  do a symlink to var/www
and you go[/QUOTE]


Sorry for being a totall newb to this, but I have done a search on these forums for an explanation of symlink. Even the results from searching for "symlink" ended up with posts with no reference to the word "symlink".


I too have just installed phpBB2 and have the same problem. nothing in my var/www folder but do see it in /usr/share/phpBB2.


Much obliged to anyone who can help me on this matter.

---

### Post by Scorpuk on 2006-05-28
Anyone?

---

### Post by doog on 2006-07-15
> **joshchernoff said:**
> Where are the files for the phpbb templets at? I dont see anything in the /var/www folder.

they are in /usr/share/phpbb2/site

If you want them somewhere else then you have a few choices, you can change your apache2 config file( /etc/apache2/site-exists/000-default or something like that ) so that it points to where your files really are.

or

you can copy those files to your current web home:
sudo cp -a /usr/share/phpbb2/site /var/www/forum

or

you can create a link in /var/www which 'points' to the other location:
sudo mkdir /var/www/forum
sudo ln -s /usr/share/phpbb2/site /var/www/forum

If you change the apache config then your URL would be [http://localhost/index.php](http://localhost/index.php)
but if you now have your phpbb site as a folder( link or otherwise ) under /var/www then your URL would be [http://localhost/forum/index.php](http://localhost/forum/index.php).

got it?

---

### Post by az on 2006-07-15
[https://help.ubuntu.com/community/PhpBB2](https://help.ubuntu.com/community/PhpBB2)

---

