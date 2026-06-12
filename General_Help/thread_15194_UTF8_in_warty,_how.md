---
title: "UTF8 in warty, how?"
date: 2005-02-12
forum: General Help
---

### Post by Leo Torjeman on 2005-02-12
hello, i am working with files in hebrew in ubuntu so i need to know how to change the locale to UTF8
 
 thanks,
 
 Leo Torjeman

---

### Post by cblack on 2005-02-12
```
sudo dpkg-reconfigure locales
``` 

select the encoding you want and then select it as the default.

---

