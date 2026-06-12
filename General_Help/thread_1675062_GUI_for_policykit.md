---
title: "GUI for policykit?"
date: 2011-01-24
forum: General Help
---

### Post by melrokz on 2011-01-24
When a user mounts an internal disk on my computer, a window pops up asking for an admin password, as attached below.

When I click on the links, nothing happens.
In previous editions of Ubuntu, there was a GUI for this called "Authorisations". But this edition (10.10) seems to lack that. 

How can I set permissions for users to allow a user to mount internal disks? Is there any way to download the GUI? 
Thanks in advance for your assistance.

---

### Post by melrokz on 2011-01-25
Does anyone understand what I've posted?
I guess there are no quick answers for this query...

---

### Post by Smart Viking on 2011-01-25
```
sudo apt-get install mountmanager
```

---

### Post by melrokz on 2011-01-29
Someone please help me understand if it is a PolicyKit issue and if there's a GUI available to set permissions...

---

### Post by HermanAB on 2011-01-29
There is no Policykit GUI anymore.  The whole thing changed, so the GUI became obsolete.  However, you can edit the polkit files in /etc by hand if you must.

---

