---
title: "Wordpress local installation problem"
date: 2010-03-26
forum: General Help
---

### Post by Halibutt on 2010-03-26
I recently upgraded to a new machine (and new Ubuntu 9.10). Now I'm trying to install Wordpress locally to test my site's skin before I publish it. 

At first I tried the most simple method suggested in one of the threads:
```
sudo apt-get install wordpress
```

However, it seems the installation went fine, but there was nothing in my var\www folder, so I decided to go the hard way. 

I started the process explained in [this tutorial]("http://www.supriyadisw.net/2006/12/wordpress-installation-on-ubuntu-with-lamp"). All went fine, navigating to [http://127.0.0.1/](http://127.0.0.1/) shows that Apache runs just fine. 

However, when I navigate to either [http://127.0.0.1/wordpress](http://127.0.0.1/wordpress) or more specifically to 127.0.0.1/wordpress/wp-admin/install.php, Firefox tries to download some .phtml file instead of running it. Previously under 8.04 I had the same problem, but found a workaround by using Opera (it worked just fine). However, now even Opera tries to do the same. 

Any ideas what I'm doing wrong?
Cheers

---

### Post by Halibutt on 2010-03-26
[s]Found a solution, please delete this thread (in short it was a problem with WP settings and not with LAMP or Ubuntu). Sorry for the fuzz.
Cheers[/s]

EDIT/ It seems the problem was not with Wordpress in the end as it returned upon system restart. Any ideas how to solve the issue?

---

