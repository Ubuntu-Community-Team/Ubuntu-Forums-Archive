---
title: "Samba problem"
date: 2009-11-30
forum: General Help
---

### Post by samcoles on 2009-11-30
Hi, I've posted this again as I think I put it in the wrong forum last time.

I've set up a samba server on a computer running debian under the stairs and mounted it on my ubuntu desktop on the PC in my room by putting the mount command in /etc/fstab, the sambashare folder contains my music right now and is working. The sambashare is chown'd to the user that logins to the samba server and chmod'd rwx to the user. It is at /sambashare on the debian computer.

I can copy files to it, however, if I try to drag a folder containing say a bunch of image files to it, then it creates the directory but this new directory does not have write permissions for the user so there is then an error trying to copy the files into the newly created directory. I can of course just chmod this from the debian computer but that's not the point, is it?

What I want is for all directories and files created in the sambashare from my PC upstairs to be chown'd by the correct user and chmod'd correctly... I can post my config file if need be.

Any help much appreciated, be gentle, I am fairly new to this linux lark. Thanks.

---

### Post by samcoles on 2009-11-30
This is my smb.conf in case it's important


[global]
workgroup = WORKGROUP
netbios name = HALLWAY
[sambashare]
path = /sambashare
browseable = yes
writeable = yes
valid users = numbersix
read only = no
write list = numbersix

---

### Post by Leppie on 2009-11-30
I think you have to mount the share with the dmask option in fstab.

---

### Post by samcoles on 2009-11-30
//192.168.1.68/sambashare /home/sam/Desktop/samba cifs username=numbersix,password=xxx,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0


This is the mount command, how would I go about modifying this? I do think it is a problem with the Ubuntu end of things as my housemate copied me a folder of music from his Vista machine onto it no problems.

---

### Post by Leppie on 2009-11-30
Try the following:
```
//192.168.1.68/sambashare /home/sam/Desktop/samba cifs guest,rw,iocharset=utf8,file_mode=0777,dir_mode=0777,noperm 0 0
```

---

### Post by samcoles on 2009-12-01
I changed the config file to allow guests too and it's all working fine with your mount command now. Thankyou very much. Didn't really need the user with the password anyway.

Any suggestions as to why this was? Anything to do with the user accessing it being my user 'sam' on the ubuntu PC and not the numbersix user I created on the server machine?

---

