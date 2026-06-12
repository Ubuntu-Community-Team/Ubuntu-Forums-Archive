---
title: "Adding a share to a panel"
date: 2010-11-10
forum: General Help
---

### Post by claydon on 2010-11-10
Hi, 

Looking for information on how to add an icon to a panel that opens a windows share that I have mounted. 

Also when I restart my PC the share seems to drop, is there a way to make them persistent.

Thanks for your help

---

### Post by Ghost_Mazal on 2010-11-10
Here is an example of a line you can add to your /etc/fstab file that will mount your share outomatically to a specific folder you create for it everytime your pc boots :
 
```
 
//servernameorip/sharename /mnt/foldername cifs username=usernameofshare,password=passwordofshare 0 0
 

```
 
From there it's as easy as creating a normal shortcut that points to /mnt/foldername
 
/mnt/foldername can be any folder you create and remember to first give your own user full access rights to that folder you create

---

### Post by Ghost_Mazal on 2010-11-10
I forgot to add , after you added the entry into /etc/fstab and saved you don't need to reboot to test. Simply execute the command:
 
```
 
sudo mount -all

```
 
then just cd to your /mnt/foldername and see if you can see the contents off your share. If not you made a little typing error somewhere.

---

### Post by Morbius1 on 2010-11-10
If you're used to how it works now you could just add a launcher to the panel:

Right Click the panel
Select: Add to Panel
Select: Custom Application Launcher
Command: 
```
nautilus smb://machine_name/Share_name
```Change those to your specific machine name or ip address and specific share name.

---

