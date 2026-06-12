---
title: "SAMBA please help me modify my files using 10.10"
date: 2011-07-08
forum: General Help
---

### Post by mikehenry001 on 2011-07-08
I need help with Samba. 

I have a samba server running on CentOS 5.3.
Windows can connect to it fine with my smb username and password and I can modify files with no problems. The group with rights is called "share". 

On Ubuntu 10.10 when I mount the Samba share, I have only read rights, even knowing I'm using the same credentials that I do on the Windows machine.

smbfs is installed on Ubuntu.
Mount strings I've tried:
sudo mount -t smbfs -o username=mhenry //192.168.0.51/samba /home/mhenry/sambamount

sudo smbmount //192.168.0.51/samba /home/mhenry/sambamount -o username=mhenry,password=mysecret,uid=500,mask=777,workgroup=workgroup

On this last try, I threw in everything I could find. the uuid is the uuid on the centos box.

---

### Post by Morbius1 on 2011-07-08
The uid is your own on the Ubuntu box not the CentOS box. And there is no "mask" or even a "umask".

To bring this up to date give this a shot:
```
sudo mount -t cifs -o username=mhenry,password=mysecret,uid=1000,dir_mode=0777,file_mode=0666,nounix //192.168.0.51/samba /home/mhenry/sambamount
```Having a uid=1000 and a file_mode / dir_mode = 0666 / 0777 is overkill but ...........

---

### Post by mikehenry001 on 2011-07-08
SWEEET!!!!  Thank you sooo much. Works like a charm!

---

