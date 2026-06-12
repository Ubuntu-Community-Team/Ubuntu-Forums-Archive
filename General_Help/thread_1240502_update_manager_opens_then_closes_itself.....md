---
title: "update manager opens then closes itself...."
date: 2009-08-14
forum: General Help
---

### Post by MacKai on 2009-08-14
update manager opens then closes itself.... it's open for less than a second, dosent mater if I click on the notification icon or right click and start from the drop down menu, or open from System > Admin.  Synaptic package manager is doing the same thing...


any ideas?



Ken V

---

### Post by soapBAR2 on 2009-08-14
Open a terminal, and please post the results of

```
sudo apt-get update ; sudo apt-get upgrade 
```

(It updates your repository and then installs new updates).

---

### Post by MacKai on 2009-08-14
that did it.... downloaded the updates and update manager and synaptic  both work properly ....thanks.....


MacKai

---

