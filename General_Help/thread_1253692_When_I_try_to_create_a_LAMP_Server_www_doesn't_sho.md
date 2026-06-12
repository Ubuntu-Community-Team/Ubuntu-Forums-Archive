---
title: "When I try to create a LAMP Server www doesn't show up in var"
date: 2009-08-30
forum: General Help
---

### Post by jigglypuff on 2009-08-30
This would be my second time trying to create a lamp server. The first time I deleted the www in var with some terminal command because I couldn't delete it normally. And the second time I try to create a LAMP server it won't create the www folder Please Help :):)

---

### Post by uylug on 2009-08-30
> **jigglypuff said:**
> This would be my second time trying to create a lamp server. The first time I deleted the www in var with some terminal command because I couldn't delete it normally. And the second time I try to create a LAMP server it won't create the www folder Please Help :):)

Are you running an Ubuntu Server or an Ubuntu running Gnome? If you're running gnome, why don't you set up your LAMP server using Synaptic? Click on Edit -> Select Packages by Task and then choose LAMP Server. It will get all the necessary packages for you and configure it correctly.

Also, what do you get if you click this link?

[http://localhost](http://localhost)

If it says page not found or something, try this:

Create the /var/www directory
```
sudo mkdir /var/www
```

Create a test page
```
sudo echo It Works > /var/www/index.htm
```

Check if its working
[http://localhost](http://localhost)

---

### Post by jigglypuff on 2009-08-30
Thanks a lot :guitar:

---

