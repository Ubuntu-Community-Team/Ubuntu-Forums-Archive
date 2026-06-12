---
title: "/etc/aliases"
date: 2012-06-07
forum: General Help
---

### Post by lo.j on 2012-06-07
hi all.
i have a problem i never had before and i cannot understand the cause...

i got a new ubuntu server 12.04 installation and i'm using postfix with mutt.

i populated **/etc/aliases** with:
```
postmaster: root
testuser: address@domain2.com
```
then i run both **sudo newaliases** and **sudo service postfix restart**...

i also have:
```
domain1.com
```
in **/etc/mailname**

but when i run:
```
$ echo "test" | sudo mutt -s "test" -- testuser
```
postfix sends it to **testuser@domain1.com** instead of **address@domain2.com**!

am i missing something?
thanks a lot.

---

### Post by lo.j on 2012-06-07
reached third page in three hours! :)
this forum is too crowded... bump!

---

### Post by VMC on 2012-06-07
It may be your use of aliases is foreign to most people. My use of aliases is local. As in bash alias. In searching, I see no reference to how you want to use it.

---

### Post by lo.j on 2012-06-08
> **VMC said:**
> It may be your use of aliases is foreign to most people. My use of aliases is local. As in bash alias. In searching, I see no reference to how you want to use it.

[man aliases](http://unixhelp.ed.ac.uk/CGI/man-cgi?aliases+5)

---

### Post by lo.j on 2012-06-08
please... anyone? :roll:

---

### Post by kanikilu on 2012-06-08
I know the kind of aliases you are talking about, but I've never set that up myself, sorry.

Maybe the server forum would be more appropriate? You'd certainly get bumped off the main page less often :p

---

### Post by lo.j on 2012-06-08
> **kanikilu said:**
> Maybe the server forum would be more appropriate?yes, maybe it could be a good idea...
could i ask a moderator to move this thread please? :)

---

### Post by lo.j on 2012-06-12
solved commenting out mydestination setting in /etc/postfix/main.cf

---

