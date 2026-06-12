---
title: "Apache issue"
date: 2010-05-25
forum: General Help
---

### Post by sixstringssteve on 2010-05-25
Quick Apache question.  I have Apache installed currently and it works fine.  I jsut installed XAMPP because I need the PHP and MySQL options.  The problem I have now is Apache does not point to the htdocs file, it still looks for the html file at /var/www.  I am sure there is a place in httpd.conf that has this, but I can't seem to find it.  Can anyone help a brother out here?

---

### Post by WorMzy on 2010-05-25
I've never used XAMPP, but if you want to install Apache/MySQL/PHP, then what I would do would be to run 'sudo tasksel install lamp-server'. Perl, Python and Ruby support can be added after this operation by running 'sudo apt-get install libapache2-mod-perl2 libapache2-mod-python libapache2-mod-ruby'.

Quick, simple, and easy.

---

### Post by sixstringssteve on 2010-05-28
thank you, I'll be trying this one out.

---

