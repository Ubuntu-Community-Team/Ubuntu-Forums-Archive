---
title: "i have to install samba server on a linux server from my local pc.how can i do that."
date: 2010-01-06
forum: General Help
---

### Post by Ashishkhandelwal on 2010-01-06
I have been given a task to install samba server from my local PC in an another PC which is a linux server.The linux server is in my own comapny and i have been given its ip address and root login password.I dont know how to install that samba server from my own PC.Can anyone help me please???

---

### Post by bodhi.zazen on 2010-01-06
So, I assume you need to ssh into the linux server and install samba.

Assuming you are in windows you can ssh in with putty.

this  will bring you to a command line interface.

Then

apt-get update 
apt-get install samba

See also :

[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

---

### Post by Ashishkhandelwal on 2010-01-06
I have logged in the server through SSH but the server is having suse linux OS and i dont know what is the process in this os to install samba server so if anyone can help me then i will be very grateful.

---

### Post by bodhi.zazen on 2010-01-06
[http://susewiki.org/index.php?title=Setting_up_Samba](http://susewiki.org/index.php?title=Setting_up_Samba)

---

