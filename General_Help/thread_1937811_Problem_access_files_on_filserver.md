---
title: "Problem access files on filserver"
date: 2012-03-08
forum: General Help
---

### Post by robinasa on 2012-03-08
Hello,

I have installed ubuntu 11.10 and Samba.
I have no problem sharing the files, and I can easy find the fileserver from my other computer via LAN.

But when I click on the shared folder from the network and type in my user/pass (Ubuntu username, same as i log on with in ubuntu) I get access denied..


Got an idea?

---

### Post by Morbius1 on 2012-03-08
Did you add that username to the samba password database:
```
sudo smbpasswd -a username
```

---

### Post by robinasa on 2012-03-08
No, can`t I use my username and pw I use on ubuntu?

---

### Post by Morbius1 on 2012-03-08
You can but unlike Windows there's a difference between the Linux Login user and the Samba user. You can connect the 2 different types of users with the smbpasswd command.

So if your linux login user name is robinasa then connect the two users together and give him a samba password that matches the login password.
```
sudo smbpasswd -a robinasa
```It will first ask you for the sudo password and then it will ask you for the samba password that you want to use.

---

### Post by robinasa on 2012-03-09
Thanks! SOLVED:popcorn:

---

