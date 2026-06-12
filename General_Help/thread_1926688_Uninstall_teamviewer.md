---
title: "Uninstall teamviewer"
date: 2012-02-16
forum: General Help
---

### Post by Chelidze on 2012-02-16
I needed teamviewer on ubuntu 11.10 x64 and i installed teamviewer.deb version 
 know i do not need this software but i can not uninstall it can some one help me


                                thank you in advance

---

### Post by lowbudgetlaptops on 2012-02-16
hello try typing in terminal sudo apt-get remove teamviewer

---

### Post by Chelidze on 2012-02-16
> **lowbudgetlaptops said:**
> hello try typing in terminal sudo apt-get remove teamviewer

thank you for your reply but it did not work :(


```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package teamviewer

```

this is what i got

---

### Post by polki@mac.com on 2012-02-17
Type:
sudo apt-get remove teamv
and then hit tab and it should auto-complete.

I've got both teamviewer6 and teamviewer7 installed so I had to hit tab twice before it showed me what I had to type to get rid of the right one.

---

### Post by Vishal Agarwal on 2012-02-17
dpkg -l | grep team
 you will get the installed package name and then u can apt-get remove  easily that.

---

### Post by Chelidze on 2012-02-17
> **polki@mac.com said:**
> Type:
sudo apt-get remove teamv
and then hit tab and it should auto-complete.

I've got both teamviewer6 and teamviewer7 installed so I had to hit tab twice before it showed me what I had to type to get rid of the right one.


thank you very much it worked

---

