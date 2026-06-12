---
title: "apt-get and evolution interface language"
date: 2006-04-14
forum: General Help
---

### Post by knakkerbakker on 2006-04-14
During the Kubuntu installation I chose Dutch as the system language.
After a while I set the language to English using kcontrol.
Everything is in English now, as desired, except for Evolution and the apt-get tool in the console.

Evolution has only partly switched to English after changing the KDE language. The settings dialog, and the 4 switch buttons in the lower left corner haven't switched to English.

I hope someone knows how to get the English interface working for Evolution and apt-get.

Thanks in advance.

---

### Post by fdoving on 2006-04-14
Hi.
First run:
```

dpkg-reconfigure -plow locales

```
Choose the languages you want to have available. 


Next edit /etc/environment, change the LANG variable to the language you want.

Here is mine, set to the default US english, as an example:
```

LANG=en_US

```


- Frode

---

### Post by knakkerbakker on 2006-04-15
Evolution and Apt-get now are fully in English like the rest of the system.:D

Thanks for your help.

---

