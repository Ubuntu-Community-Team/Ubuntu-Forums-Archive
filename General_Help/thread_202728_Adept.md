---
title: "Adept"
date: 2006-06-23
forum: General Help
---

### Post by souteneur3190 on 2006-06-23
There was an error commiting changes. Possibly there was a problem downloading some packages or the commit would break packages. 

I just went from ubuntu to kubuntu and that is the error i get when ever i try to install anything using adept.

---

### Post by aysiu on 2006-06-24
Can you post the output of this command? ```
sudo apt-get -f install
```

---

### Post by souteneur3190 on 2006-06-24
[QUOTE=aysiu]Can you post the output of this command? ```
sudo apt-get -f install
```[/QUOTE]

(Reading database ... 95680 files and directories currently installed.)
Removing scim-gtk2-immodule ...
/var/lib/dpkg/info/scim-gtk2-immodule.postrm: line 8: /usr/sbin/update-gtk-immodules: No such file or directory
dpkg: error processing scim-gtk2-immodule (--remove):
 subprocess post-removal script returned error exit status 1
Errors were encountered while processing:
 scim-gtk2-immodule
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by ajgreeny on 2006-06-24
Personally, I prefer synaptic to adept and seldom use the latter even when it tells me there are updates available.  Perhaps it's just that I know synaptic better but it gives more information, I think and I'm just more comfortable with it.

---

