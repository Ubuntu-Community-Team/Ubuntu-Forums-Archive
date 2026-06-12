---
title: "Setting permissions in file sharing"
date: 2011-08-08
forum: General Help
---

### Post by bdemers on 2011-08-08
2 computers, Ubuntu 10.04 and Ubuntu 8.04.  I have 2 folders named In and Out.  Out I have set up on 10.04 for guest use. I am able to transfer files to 8.04 from that folder.  Trying to set up In for a specific user to modify files.  This requires a login.  Both computers have the same user name and both have the same password.  I set the file permissions automatically from 10.04 when electing to share In for allowed modiying.  When trying to access In using 8.04, a password request window is generated with the user name already showing, and the domain name filled in as "Workgroup".  The user name that shows is my login name, by the way.
Entering password fails authentication.  This is a wireless connection.

I am not allowed access, any hints? Found nothing in the log files.

---

### Post by cbruce8 on 2011-08-08
Sounds like an smb(MS) share. 'Workstation' means an identical username on a pc will not be the same as the name on a different pc. Personally I would use a non-smb file share. I believe NFS is available.

---

### Post by Morbius1 on 2011-08-08
> I set the file permissions automatically from 10.04 when electing to  share In for allowed modiying.  When trying to access In using 8.04, a  password request window is generated with the user name already showing,  and the domain name filled in as "Workgroup".  The user name that shows  is my login name, by the way.It sounds like you are only missing one step.

You already have a local user on 10.04 with a local login username and password but you didn't give him a samba password:
```
sudo smbpasswd -a user-name
```It will first ask you for the sudo password then it will ask you for a samba password for "user-name". That's the password that the 8.04 user has to use to gain access.

---

