---
title: "xampp + apache + Directory + media/HDD = Error 403"
date: 2010-03-20
forum: General Help
---

### Post by canado on 2010-03-20
Hello there


I just installed xampp, if I run it with the basic configuration, everything is fine.

Now I want the localhost to go to a directory on another hard-drive
(that I will use exclusively for svn)

I change the httpd.conf like that


DocumentRoot "/media/HD-SVN"


<Directory "/media/HD-SVN">   
    Options Indexes FollowSymLinks ExecCGI Includes
    AllowOverride All
    Order allow,deny
    Allow from all
</Directory>

Now when I go to [http://localhost/](http://localhost/) it "seems" to work as I don't have any error, but I can't see the directories inside

and when I try to access the SVN directory I have a 403 error

So I went inside /media/HD-SVN and try to change the permissions
using super nautilus and even in a terminal using chmod -R 666 SVN
but I still got the problem

Any idea ??

in fact maybe I m wrong but I want to install a svn server so I need a http:// address to create a repository that's why I installed xampp, so if I m not in the good direction, please point me to a solution

thanks in advance

---

### Post by roccivic on 2010-03-20
did you try 777?

---

### Post by tuguix on 2011-07-31
got the same with LAMP. It works out of the box on the installation disk but wont work on the second hdd or usb ones .:( Tried everything the only thing i dont know is howw to set an entire hdd permission, or how to add it to fstab...  :confused::confused::confused::confused::confused::confused:

---

