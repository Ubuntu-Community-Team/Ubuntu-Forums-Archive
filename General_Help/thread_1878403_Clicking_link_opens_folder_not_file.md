---
title: "Clicking link opens folder not file"
date: 2011-11-09
forum: General Help
---

### Post by kainalu on 2011-11-09
Hello all,

I noticed an odd behavior recently. I use Natty Classic desktop, and recently noticed that when I click a link to open a file, instead of opening the file directly, it shows it in Nautilus instead. 

So if I click a file in my indexer, or gnome do, or some such, it will open the folder containing the file and highlight it. Up until very recently it would open the file.

I'm sure it is just an association, but I don't know how to change it. Any ideas?

---

### Post by alexyz on 2012-01-16
short answer : uninstall exo

HOWEVER I believe this breaks xfce, so don't do it if you're using xfce as well as gnome.  this is an old post but I had a very hard time finding the answer to this question.  finally found this : [https://bbs.archlinux.org/viewtopic.php?pid=882193](https://bbs.archlinux.org/viewtopic.php?pid=882193)

probably there is a better solution but if you don't need xfce this works.  in my case it was the following:

> 
Completely removed the following packages:
exo-utils
libexo-1-0
libexo-common
libexo-helpers

---

