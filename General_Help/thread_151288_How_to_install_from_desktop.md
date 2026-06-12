---
title: "How to install from desktop ?"
date: 2006-03-27
forum: General Help
---

### Post by terryfox on 2006-03-27
Hello .

I have try to load amsn messenger from the add app area and when I try to use it? It said that there a newer version available , So downloaded onto the desktop , Can someone explain how to load it ? Or even where I can read how its done ? 

TIA ...

---

### Post by Jason_25 on 2006-03-27
You might want to post a link to the new version you downloaded.

---

### Post by aysiu on 2006-03-27
Assuming you downloaded the Ubuntu version (see attached screenshot), open a terminal (Applications > Accessories > Terminal) and type ```
cd Desktop
sudo dpkg -i amsn_0.95-3.ubuntu.deb
```

---

### Post by stoeptegel on 2006-03-27
How is this update package stuctured, in a tarball(*tar.gz for instance) ? Also, are there any INSTALL or readme files between the files?

---

### Post by terryfox on 2006-03-27
Hi ... Yes its from the same place and same version Aysiu has listed in the image , Well I just installed and its working , Thanks

BTW : whenever I am able to use programs for this OS and I install the program onto my desktop , What are the steps usually I have to perform ? So from I know I have to place this in the terminal 

cd Desktop 

What usually comes after that ? Is there somewhere that I can read about it ? Thanks

---

### Post by terryfox on 2006-03-27
Is this the correct code to install a program thats on the desktop ?X is the name of the program / file 

cd Desktop
sudo dpkg -i XXXXXXXX.deb

Thanks

---

### Post by aysiu on 2006-03-27
This will tell you what you need to know:

[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

Generally, though, you'll never be more than six months behind the latest release if you just keep upgrading to the latest version of Ubuntu. You don't have to keep downloading the latest version of each program separately to your desktop.

---

### Post by terryfox on 2006-03-27
Aysiu >>> Thank you , much appreciated :cool:  Now to try to figure out the more diffecult problem I have lol

---

