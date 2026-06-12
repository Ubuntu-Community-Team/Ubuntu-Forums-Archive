---
title: "wlan lags (need help) I think thats easy :P"
date: 2010-01-29
forum: General Help
---

### Post by matiking550 on 2010-01-29
Emm hello
I playing role playing games and my wlan all 5 or  2  min search a new router and than i have lag about 2-3 sek 
somone know how i can fix it ? :razz:



Please help , and thanks.



Sorry for my english . I'm 14 :razz:.:popcorn:
dont work  (vista anty lag)
dont work  (wirles zero shutdown)

---

### Post by llawwehttam on 2010-01-29
This worked for me:

```
sudo apt-get install linux-backports-modules-2.6.31-14-generic linux-backports-modules-karmic linux-backports-modules-karmic-generic linux-backports-modules-wireless-karmic-generic
```
Then reboot.

---

### Post by matiking550 on 2010-01-29
ok very thanks
and what is reboot ?
 XD

---

### Post by matiking550 on 2010-01-29
one problem :(
he cant find it :
E: Konnte Paket linux-backports-modules-2.6.31-14-generic nicht finden

---

### Post by audiomick on 2010-01-29
My synaptic package manager can find it.

Have you got all the package sources enabled?
system> administration> synaptic package manager
system> verwaltung> synaptic paketverwaltung

in the menu "Einstellungen", probably "preferences" in English
select "Paketquellen", english "package sources"
look on the first tab
and make sure all the boxes are ticked, except "quelltext", english "source code"

Reboot means start the computer again. Neustart.

---

### Post by llawwehttam on 2010-01-29
Ok try replacing the kernel name with your's. Type ```
uname -r
```to find your kernel.

EDIT: Maybe audimick can help you more as my german is awful. I can say 'gutentag' und 'Auf wiedersehn' and thats about it.

---

### Post by matiking550 on 2010-01-29
thats worked :)))))
sudo apt-get install linux-backports-modules-2.6.28-11-generic
im very thanks 
=))))))))))))

---

### Post by matiking550 on 2010-01-29
kk
now im reboot 
see u

---

### Post by matiking550 on 2010-01-29
oke it works no lags :)

---

### Post by llawwehttam on 2010-01-29
Glad thats fixed for you.

---

