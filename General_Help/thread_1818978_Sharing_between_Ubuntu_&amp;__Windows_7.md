---
title: "Sharing between Ubuntu &amp;  Windows 7"
date: 2011-08-05
forum: General Help
---

### Post by jolian ramos on 2011-08-05
[SIZE=4]Sharing between Ubuntu &  Windows 7
i get this message when i try to connect from Ubuntu to a shared folder on my Windows 7 

This is the message i get 
[U]
[[IMG]http://img109.imageshack.us/img109/486/screenshotsc.jpg[/IMG]]("http://imageshack.us/photo/my-images/109/screenshotsc.jpg/")

Uploaded with [ImageShack.us]("http://imageshack.us")
[/U] [/SIZE]

---

### Post by Furball588 on 2011-08-05
Assuming this is homegroup, you probably need to be using HomeGroupUser$ along with your homegroup password to access the share.

---

### Post by Morbius1 on 2011-08-05
It could also be a gvfs thing internal to nautilus. See if you have the following packages installed:
```
sudo apt-get install gvfs-backends
sudo apt-get install gvfs-fuse
```And add yourself to the fuse group:
```
sudo gpasswd -a user-name fuse
```Logout and login again for the group membership to change and try to access the share again.

---

### Post by jolian ramos on 2011-08-06
> **Furball588 said:**
> Assuming this is homegroup, you probably need to be using HomeGroupUser$ along with your homegroup password to access the share.
I don't know which password you are talking about i use in Ubuntu Places====> connect to server ====> then i enter windows share =====> and enter ip of my windows 7 pc  and press connect , it asks me about the password that i use for the windows & to login and i enter it , but it asks me to enter a password to unlock network or something like that , but i don't know which password it talks about so i enter my ubuntu password root one and then this message in picture appears to me .. so what do you think out of this ?? i hope u can help with some more details ... thanks

---

### Post by jolian ramos on 2011-08-06
??

---

### Post by jolian ramos on 2011-08-06
> **Morbius1 said:**
> It could also be a gvfs thing internal to nautilus. See if you have the following packages installed:
```
sudo apt-get install gvfs-backends
sudo apt-get install gvfs-fuse
```And add yourself to the fuse group:
```
sudo gpasswd -a user-name fuse
```Logout and login again for the group membership to change and try to access the share again.
gvfs is istalled , all of it

---

