---
title: "Can't create file /etc/udev/rules.d/70-android.rules"
date: 2011-06-19
forum: General Help
---

### Post by webusr1 on 2011-06-19
All,
I need to create filename 70-android.rules in the directory  /etc/udev/rules.d/

I have Adm privileges in my user account properties, but when I use sudo to create this file the Ubuntu OS does not allow me the privilege... :(

I am running Ubuntu 10.04 LTS and here's the Terminal output below:

daddy@gatomon-laptop:/etc/udev/rules.d$ sudo cat > 70-android.rules
bash: 70-android.rules: Permission denied

daddy@gatomon-laptop:/etc/udev$ ls -l
total 8
drwxr-xr-x 2 root root 4096 2011-03-16 18:03 rules.d
-rw-r--r-- 1 root root  218 2010-04-19 04:30 udev.conf

Any help would be greatly appreciated.

Thanks!

---

### Post by nothingspecial on 2011-06-19
Assuming this file is going to have some sort of text included....


.....create it with nano

```
 sudo nano 70-android.rules
```

Then you can put the text in it at the same time :D

---

### Post by webusr1 on 2011-06-19
Cool. Thanks!!! That worked! I used vi instead though. BUT WHY didn't the following work???

sudo cat > filename

---

