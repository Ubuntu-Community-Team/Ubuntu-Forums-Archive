---
title: "Show installed .deb libraries etc."
date: 2006-04-24
forum: General Help
---

### Post by 999.michael on 2006-04-24
Is there any way that i can get a list of the .deb libraries and applications that i have installed on my computer (including ones from base installation)? whenever i download a new application, i end up having to install all of the required packages, often reinstalling them over and over again, because i dont know what i have installed. if i dont download any i often get errors and so install is corrupted.

thanks in advance :KS

---

### Post by Ramses de Norre on 2006-04-24
dpkg -l
you can pipe it into grep because it's a pretty long list, ```
dpkg-l|grep package_name
```

---

### Post by 999.michael on 2006-04-25
ok thanks

---

### Post by cypresstwist on 2006-04-27
for n in `dpkg-query -W --showformat='${Package} '`; do if ( apt-cache show $n | grep -q "^Filename:.*/**universe**/") ; then echo $n; fi; done

replace "universe" with your fav. repository.

---

