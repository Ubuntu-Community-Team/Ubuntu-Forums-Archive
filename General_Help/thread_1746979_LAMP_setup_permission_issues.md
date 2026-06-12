---
title: "LAMP setup permission issues"
date: 2011-05-02
forum: General Help
---

### Post by HandleWithCare on 2011-05-02
I'm breaking my head on this.I want to create a development environment. This means that I want to be able to create/change files myself, but php should be able to do the same. 

I installed a lamp-stack using tasksel. Afterwards I installed phpmyadmin. So far so good. Going to [http://localhost](http://localhost) shows "it works".

Then I created a folder /home/hwc/www and created a new apache site called hwc, disabled default and enabled hwc that points to /home/hwc/www and has the directive AllowOveride All set.
But when I go to [http://localhost](http://localhost) know I get a 403 Permission denied error. 
I've tried several trings like changing ownership of /home/hwc/www to www-data:www-data, to hwc:www-data, to hwc:hwc, but all to no avail. Even adding www-data to group hwc and hwc to group ww-data did not help. According to other posts at least on of these solutions should have worked, but it did not.
I could probably fix it by letting apache run as hwc, but that doesn't seem right.

---

### Post by HandleWithCare on 2011-05-04
This was fixed by setting permission on /home/hwc/ to 751

---

### Post by dragonfly41 on 2011-05-04
If you search "apache2 403" there are lots of posts in this forum ..

here is just one [SOLVED]

[http://ubuntuforums.org/showthread.php?t=1745500](http://ubuntuforums.org/showthread.php?t=1745500)

---

### Post by HandleWithCare on 2011-05-04
Solved threads with similar title doesn't always mean a working solution. In this case my solution was to do something else.

---

