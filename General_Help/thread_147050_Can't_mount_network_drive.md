---
title: "Can't mount network drive"
date: 2006-03-19
forum: General Help
---

### Post by Granduke on 2006-03-19
I'd like to mount my music folder from a MythTV box to my ubuntu box.
I have no experience with fstab.  From reviewing posts I came up with 
 ```
//192.168.0.5/mythtv/myth/music    /mnt/home/test   smbfs   auto,user=mythtv,uid=mythtv,   unmask=000   0   0
```

Is this wrong or do I have to do something else.  I go to /mnt/test and the folder is not linked.  Samba seems to be working between the machines.

thanks

---

### Post by Ramses de Norre on 2006-03-19
I have totally no experience with this, but I think 'uid=mythtv' is odd, shouldn't that be the user id? So a number? And is the ',' behind it necessary?

---

### Post by Bradl3yJ on 2006-03-19
Try this for read/write access:

```
//192.168.0.5/mythtv/myth/music    /mnt/home/test   smbfs   credentials=/root/.smbcredentials,dmask=777,fmask=777   0      0
```


Then be sure to create the file:

```
sudo gedit /root/.smbcredentials
```

with this content:
```
username=myusername
password=mypassword
```


Replacing myusername and mypassword with the proper username and password. If your samba server is anonymous, I don't know how to connect to it, but try the username and password for one of the administrator accounts.

Then remount:

```
sudo mount -a
```


Let me know if that works for you.

---

### Post by Granduke on 2006-03-19
Hi Brad,
   
           I've tried your suggestion.  Thanks for your help.  I now get:

warning: no final newline at the end of /etc/fstab
Could not resolve mount point /mnt/home/test

When trying to remount.

---

### Post by Granduke on 2006-03-19
After soon more searching (half an afternoon's worth) I found instructions that worked for me at:[http://kudos.berlios.de/kf/kisimlar/windows.html#netmntman]("http://kudos.berlios.de/kf/kisimlar/windows.html#netmntman")

---

