---
title: "Drupal address / URL"
date: 2011-10-15
forum: General Help
---

### Post by gunksta on 2011-10-15
I am setting up a home server for the first time and decided to install drupal 6 from the repos. I followed the directions in the README.Debian file and I am pleased to say that the initial setup was pretty easy.

But, after the initial setup, drupal / apache are set up such that my drupal site is:

[www.my_url.com/drupal6/]("http://www.my_url.com/drupal6/") . . .

I intend to use drupal for most of my site and would like to be able to get to the root drupal directory by just going to:

[www.my_url.com/]("http://www.my_url.com/") . . .

But, I'm not sure what the best way to do this is.

---

### Post by DogMatix on 2011-10-15
You could use a simple html re-direct.

---

### Post by akakingess on 2011-10-16
I believe to officially change that all you need to do is adjust the httpd.conf file, which should be in apache/conf/httpd.conf , now, you could also just choose to reinstall Drupal into whichever dir httpd.conf has as the "root" web directory....  Let me know if that doesn't work and we will figure it out for you....

---

