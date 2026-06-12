---
title: "ERROR 1045 (28000): Access denied"
date: 2010-12-02
forum: General Help
---

### Post by tomarmstrong on 2010-12-02
Hi, I have been following this guide to install Apache, PHP & mysql - [http://www.howtoforge.com/ubuntu_lamp_for_newbies](http://www.howtoforge.com/ubuntu_lamp_for_newbies)

When i get up to the step 'mysql -u root' I get given this error:

```
tom@tom-laptop:~$ mysql -u root
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: NO)

```

How do i overcome this?

---

### Post by TSJason on 2010-12-02
Did you set the root password as the article advised? If so you can specify the "-p" argument in your command so that it will prompt you.

---

### Post by tomarmstrong on 2010-12-02
> **TSJason said:**
> Did you set the root password as the article advised? If so you can specify the "-p" argument in your command so that it will prompt you.

Thank you, this has solved my problem. :D

---

