---
title: "Lockdown Editor"
date: 2011-03-22
forum: General Help
---

### Post by atifdarr100 on 2011-03-22
I am trying to lockdown ubuntu so that users will only have access to the browser and 1 domain.
 
I have installed the epipthany browser and the lockdown editor. It all works great
 
But how do I stop the user from just going into the lockdown editor and removing the restrictions?

---

### Post by Script Warlock on 2011-03-22
here [http://tombuntu.com/index.php/2008/05/27/how-to-lock-down-gnome/](http://tombuntu.com/index.php/2008/05/27/how-to-lock-down-gnome/)

---

### Post by matt_symes on 2011-03-22
Hi

> But how do I stop the user from just going into the lockdown editor and removing the restrictions?

Why not just change the permissions of the executable file to 444

```
sudo chmod 444 /usr/bin/pessulus
```

I'm assuming you are using Pessulus lock down editor. Even if you are not the principle is the same.

Kind regards

---

