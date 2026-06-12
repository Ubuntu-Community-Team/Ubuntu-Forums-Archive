---
title: "Apache server - 403 errors"
date: 2011-09-30
forum: General Help
---

### Post by sarahfoxnz on 2011-09-30
Hello.

I'm installing a script / PHP programme on my localhost Apache server, & am comming across an interesting problem.


I've posted on their forum too - however i'm wondering if this is a general Ubuntu/Apache issue ?


basically, i've created /localhost/directory/  - & all the files *ARE* in the correct place, however i get a 403 error each time I go into this directory.

there are no .htaccess files preventing me.

& I can create any number of directories, & have mo problems except this one

/localhost/bob/1.php - FINE

/localhost/sarahbobbygirlbpoy/1.php - Fine

/localhost/random,12325/1.php - Fine


but whenever i go /localhost/directory/1.php (my own test file) - I get 403 error.

Ps 'directory' is not the actual name of the directory...

Could this be a hidden setting somewhere within Apache ? 

& i've even renamed 'directory' to something else - No luck either


How / where can i check apache error logs ?

---

### Post by pqwoerituytrueiwoq on 2011-09-30
make sure the user *www-data* has access to read the files

---

### Post by sarahfoxnz on 2011-09-30
can you please tell me how ?

I went to the terminal, & into the directory  & chmod to 755 - that didn't work.

I moved it (the html files) into my /home/username/website/ directory So I have permission to add/delete / modify at will..

- edit :- also chamged my apache config, so the directory IS the correct one :) )


however I think this particular directory isn't readable...  - Dont know why....

---

### Post by [S|G] on 2011-10-01
Keep in mind that the Apache user (www-data) must be able to transverse all directories until it gets to the directory where your file is.

For example, if you have /srv/foo/myuser/myfile.php the user www-data must have execute permissions (+x) on /srv, /srv/foo and /srv/foo/myuser in order to be able to read the file.

---

### Post by sarahfoxnz on 2011-10-01
> **'[S|G] said:**
> Keep in mind that the Apache user (www-data) must be able to transverse all directories until it gets to the directory where your file is.

For example, if you have /srv/foo/myuser/myfile.php the user www-data must have execute permissions (+x) on /srv, /srv/foo and /srv/foo/myuser in order to be able to read the file.

OK - how do i do either of these ? 
(i'm no expert on Ubuntu & usernames etc)

1) allow www-data to access my directory

/home/USERNAME/Website_punlic_html/   (this is my directory)...  

or

2) Allow me to access the /home/www-data/ etc directory without 'sudo' etc... 

(I forget where the original directory was located)..


BUt !! - Other html / php files in MY directory can be accessed on the web - so why not this/these sub-directory ??

---

### Post by [S|G] on 2011-10-01
You can make sure that www-data can access the directories by setting their permission to 755 (meaning that the owner can read and write to the directories and other users can read their contents):

$ sudo chmod 755 /home
$ sudo chmod 755 /home/USERNAME
$ sudo chmod 755 /home/USERNAME/Website

In addition make sure that the .php file inside your Website directory is readable by apache:

$ chmod 644 /home/USERNAME/Website/file.php


If you're looking to write inside the /home/www-data/etc without having to sudo, I'd say the best way is to change its group ownership to your own group and make it group-writable:

$ chgrp yourgroup /home/www-data/etc
$ chmod 775 /home/www-data/etc

Assuming that the directory owner is www-data, both apache and you should be able to write on the directory

---

### Post by sarahfoxnz on 2011-10-01
> **'[S|G] said:**
> 
$ sudo chmod 755 /home
$ sudo chmod 755 /home/USERNAME
$ sudo chmod 755 /home/USERNAME/Website

In addition make sure that the .php file inside your Website directory is readable by apache:

$ chmod 644 /home/USERNAME/Website/file.php


Hi. that worked :)

Thank you

---

