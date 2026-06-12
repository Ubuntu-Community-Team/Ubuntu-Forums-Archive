---
title: "No hibernate option annymore !"
date: 2010-05-07
forum: General Help
---

### Post by YapperNico on 2010-05-07
I installed Ubuntu Lucid Lynx and now my Hibernate option disappeared :D
I click help and find this : 

Depending on your computer's configuration, you can also Hibernate your computer. During hibernation, less power is used, but all of the applications and documents that you have open are preserved and will still be open when you resume from hibernation. You can resume from hibernation by moving your mouse or pressing a key.

So there is an option to enable hibernate , can someone tell me where it is?

---

### Post by Sepero on 2010-06-29
Update:
I think this problem was caused for me after I resized some of my partitions.

The package 'hibernate' does not appear to be installed on my system.

---

### Post by Sepero on 2010-07-03
I got hibernation back. The problem was that my swap partition was too small (non-existent).

After getting my swap partition resized and put back into my fstab, I needed to run a few commands.

```

apt-get install hibernate
dpkg-reconfigure uswsusp

```

I used the following link to configure uswsusp
[http://www.informit.com/articles/article.aspx?p=1565701](http://www.informit.com/articles/article.aspx?p=1565701)

---

### Post by jaithehulk on 2012-09-03
Thanks for this.. even my swap partition was very small.. as I resized it the hibernation was possible!!!

---

