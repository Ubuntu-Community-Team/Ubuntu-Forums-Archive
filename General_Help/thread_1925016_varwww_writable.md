---
title: "/var/www writable"
date: 2012-02-13
forum: General Help
---

### Post by PsyclonJohn on 2012-02-13
So, I recently got into development using CodeIgniter for a client's web site which uses the framework and I wanted to test it on my Ubuntu LAMP server. The problem isn't accessing the files, because I normally create/modify/delete files using gksudo nautilus and having root access, but I want to allow Eclipse to read my /var/www path. 
[B]
Note: [/B]I want to access it from my administrator account (john).

I've tried so many different things so far, and have actually gotten real close to making /var/www readable and writeable, but haven't gotten there yet. 

As of right now, I have my user name(john) as a secondary group for www-data, and www-data as the group for /var/www

Whenever I run /var/www it is unable to view the files within /var/www at all and says they are empty and cannot write new files to the folder. I can however view files (they have locks on them) from /var/www on my user name.

If anyone can help me out with this, I'd greatly appreciate it!

Thanks,

John

---

### Post by pqwoerituytrueiwoq on 2012-02-13
look in this folder
/etc/apache2/sites-available/
you can change the folder apache2 uses for a web site in a file in there
eg make it 
/home/$USER/public_html
or /home/www-data/project-name

the way you are going i think you want to chmod to 775 for folders and 664 for files

---

### Post by PsyclonJohn on 2012-02-13
Thanks! 

Worked like a charm!

---

