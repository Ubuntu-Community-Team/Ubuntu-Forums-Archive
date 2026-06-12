---
title: "how to setup windows shared folder"
date: 2011-09-27
forum: General Help
---

### Post by johnnoj on 2011-09-27
Hello,
Here is what i have done so far and I really need your help.
sudo apt-get install smbfs
sudo mkdir /media/primaryfolders
sudo chmod 777 /media/primaryfolders
sudo nano /etc/fstab

and i added this line

//domain_ip/primaryfolders /media/primaryfolders cifs username=administrator,password=password 0 0

save and exit

and then i mount it
sudo mount -a


Great it mounted but only one problem. I cannot create folder or save any work in this folder. Please help me. I really need your help.

Thanks.

---

### Post by bodhi.zazen on 2011-09-27
Sounds as if your problem is either:

1. Your windows share is not configured properly (to allow rw access).

2. Your user name and password are wrong.

---

### Post by HermanAB on 2011-09-28
Howdy,

To debug the problem, you need to see the error messages.  So use smbclient until you got it all figured out, then do a mount.

---

