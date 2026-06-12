---
title: "you do not have the permissions necessary to view the contents of"
date: 2010-04-15
forum: General Help
---

### Post by dazzyuk on 2010-04-15
I downloaded some drivers, extracted them and tried to CD in to the folder but I am getting permission denied even though when I done the exact same thing on another system yesterday it worked fine, I have tried sudo cd my_directory I get an error saying cd: command not found. Also tried gksu but that just sits for a minutes then turns me back to where I was at /usr/src/drivers

---

### Post by r_s on 2010-04-15
> **dazzyuk said:**
> I downloaded some drivers, extracted them and tried to CD in to the folder but I am getting permission denied even though when I done the exact same thing on another system yesterday it worked fine, I have tried sudo cd my_directory I get an error saying cd: command not found. Also tried gksu but that just sits for a minutes then turns me back to where I was at /usr/src/drivers

why don't you use su - , it will ask for root's password and direct you to the root command prompt.

---

### Post by philinux on 2010-04-15
> **dazzyuk said:**
> I downloaded some drivers, extracted them and tried to CD in to the folder but I am getting permission denied even though when I done the exact same thing on another system yesterday it worked fine, I have tried sudo cd my_directory I get an error saying cd: command not found. Also tried gksu but that just sits for a minutes then turns me back to where I was at /usr/src/drivers

 What drivers?

```
cd /usr/src
``` should work without sudo

---

