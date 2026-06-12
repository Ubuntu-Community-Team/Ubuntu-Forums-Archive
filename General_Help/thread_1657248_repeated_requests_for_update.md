---
title: "repeated requests for update"
date: 2011-01-01
forum: General Help
---

### Post by rutiezer on 2011-01-01
Every few days get information about updates available to install. 
Message says
You can install 3 updates

They are firefox, firefox branding, fire-gnome-support.

I do the update which is reported as successful, then in the few days get the same message and the same updates. 

Firefox 3.5.7 is installed on Ubuntu 8.0.4.

From "About Mozilla Firefox":
Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.1.7) Gecko/20091221 Firefox/3.5.7

How do I determine what is going on?

Can supply supply extensive description shown when I click for description of each update.

---

### Post by wojox on 2011-01-01
Open a terminal and run:

```
sudo apt-get update && sudo apt-get upgrade && sudo apt-get dist-upgrade
```

Post back result's.

---

