---
title: "Connecting between Ubuntu and Fedora"
date: 2011-10-08
forum: General Help
---

### Post by var1989 on 2011-10-08
Hi

I am trying to connect two machines one has Fedora 13 and the other has Ubuntu 11.04.I have shared the files from the Fedora using Samba but i cannot view them in Ubuntu its showing an error named DBBus error .

Thanks in Advance

---

### Post by Hugh971 on 2011-10-08
How are you trying to mount the network shares? Do you have the samba client installed on your Ubuntu machine?

---

### Post by var1989 on 2011-10-08
No I thought that wont be needed as it is installed in the server . Then i should install samba in ubuntu also ...

---

### Post by Hugh971 on 2011-10-08
to mount shares as disks in Ubuntu you will need to install the samba file system

```
sudo apt-get install smbfs
```and to mount run 

```
sudo smbmount //ipofserver/share /path/to/mountpoint -o username=userwithaccess,password=userspassword
```you should be able to access them by going to file > connect to server in nautilus without installing smbfs though.

---

### Post by var1989 on 2011-10-08
I will try this out and let you know thanks !! :)

---

