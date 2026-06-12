---
title: "apt-get vs dpkg"
date: 2010-09-07
forum: General Help
---

### Post by COKEDUDE on 2010-09-07
What are the difference between apt-get and dpkg? They both seem like they do the same thing. The man pages of dpkg say apt-get is more user friendly but I don't see any differences. 

Would both of these commands do the same thing? 
```
sudo apt-get remove package
sudo dpkg -r package
```

Would both of these commands also do the same thing?
```
sudo apt-get purge package
sudo dpkg --purge package
```

---

### Post by mcduck on 2010-09-07
Yep, they would do the same thing. Apt-get uses dpkg for the actual package install/removal tasks, and simply adds all the repository-related stuff and automatic package downloading and other features on top of it. (dpkg only installs packages you have manually downloaded to your system). When it comes to uninstalling packages, it usually makes no difference which one you use. Although apt-get does have the "autoremove" option for uninstalling packages installed as dependencies, which you won't have if you use dpkg directly.

---

