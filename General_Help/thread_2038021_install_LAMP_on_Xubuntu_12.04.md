---
title: "install LAMP on Xubuntu 12.04"
date: 2012-08-05
forum: General Help
---

### Post by sweetlinux on 2012-08-05
Can I just read instructions for installing all LAMP components for Ubuntu in my Xubuntu installation?

There are many LAMP installation tutorials online, but I can't find any for Xubuntu, would it be the same?

thanks

---

### Post by Cheesemill on 2012-08-05
It will be the same. All of the packages available for Ubuntu are available for Xubuntu as well.
I usually just run the following command to install all of the necessary packages:
```
sudo apt-get install lamp-server^
```

---

### Post by sweetlinux on 2012-08-06
cool man, thanks!

---

### Post by fairysdad on 2012-08-15
Hi,

I've tried this myself but I get an error message coming up:

```
Building dependency tree
Reading state information... Done
E: Unable to locate package lamp-server
```

---

### Post by adglife on 2012-10-07
> **fairysdad said:**
> Hi,
 
I've tried this myself but I get an error message coming up:
 
```
Building dependency tree
Reading state information... Done
E: Unable to locate package lamp-server
```
 
 
You must remember to include the '^' (without quotes) after server. Use this.
 
```
sudo apt-get install lamp-server^
```
 
:guitar:

---

