---
title: "Change login manager to ubuntu 12.04's default login manager?"
date: 2012-06-21
forum: General Help
---

### Post by Luiface on 2012-06-21
I installed Lubuntu about 5 days ago, and I am getting tired of its boring style and the login screen. :mad: UBUNTU FRUSTRATES ME SO MUCH! I can't figure out how to make it look like this [IMG]http://www.extremetech.com/wp-content/uploads/2011/09/ubuntu-11.10-login-crop.jpg[/IMG]
please help 

I am using Lubuntu 12.04 if that helps

---

### Post by zombifier25 on 2012-06-21
Try running this command:
```
sudo /usr/lib/lightdm/lightdm-set-defaults -g unity-greeter
```

---

