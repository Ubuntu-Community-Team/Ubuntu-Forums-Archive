---
title: "smb root"
date: 2012-07-07
forum: General Help
---

### Post by gishaust on 2012-07-07
Hi ubuntu people,

I have create a virtual machine on my laptop that has the directory /var/www/sites

I have installed smb and what I want to do is add create a share that allows me to add data into at will. But the owner and group needing to be the same as /var/www/sites eg owner root , group root

With the rights of 775 or 777 so that the host computer will be able to access the share. I have this so far but I am not to sure how to do it? Any help would be gratefully received

[Web]
       path = /var/www/sites
       read only = No
       create mask = 0777
       directory mask = 0777

---

