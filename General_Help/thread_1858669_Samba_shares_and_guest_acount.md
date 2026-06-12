---
title: "Samba shares and guest acount"
date: 2011-10-12
forum: General Help
---

### Post by j_kubik on 2011-10-12
I am trying out samba configuration and access rights.

I have user account X and this user wants to share publicly (readonly) directory /Y/Z, that belongs to him, and has access rights drwx------. My current samba configuration for this share is

```
[X]
   comment = X directory
   path = /Y/Z
   guest ok = yes
   guest only = yes
   guest account = X
   read only = yes
```

As far as I understand samba configuration, this should map any access to this share to guest user, in this case user X, and therefore grant read access (because user X has read acces to this dir). However on attempt to mount i get 
```
root@MACHINA:/mnt# smbmount -o guest //localhost/X /mnt/test/
Warning: mapping 'guest' to 'guest,sec=none'
mount error(13): Permission denied
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)
```

If change access rights to /Y/Z directory to a bit less restrictive, (drwx--x--x) mount succedes but listing mounted dir causes Access Denied error. After going to (drwxr-xr-x), it works well, which suggests that another account is being used. Changing read only to no, mounting and touching a file shows that nobody user is being used inspite of guest account command. Does anybody know why is this happening?

Server has set 
```
map to guest = bad user
```
and
```
usershare allow guests = yes
```, although I doubt this last one has any meaning, as all shares are configured in smb.conf, so they are not usershares. I am using smbd 3.5.8 on kubuntu 11.04.

---

### Post by prodigy_ on 2011-10-12
> **j_kubik said:**
> If change access rights to /Y/Z directory to a bit less restrictive, (drwx--x--x) mount succedes but listing mounted dir causes Access Denied error.
As it should be because 'x' is generally meaningless without 'r'.

> Changing read only to no, mounting and touching a file shows that nobody user is being used inspite of guest account command.
Samba's 'guest' user is mapped to UNIX 'nobody' user by default:
[http://wiki.samba.org/index.php/Frequently_Asked_Questions#guest_access](http://wiki.samba.org/index.php/Frequently_Asked_Questions#guest_access)

---

### Post by cryptotheslow on 2011-10-12
Bear in mind that Samba **cannot **override underlying filesystem permissions.

Allowing guest access in the samba configuration will be irrelevant if the shared folder and files permission is set like drwx------ that means only the owner of said folder/files can access them regardless of what samba would like to do. Unless you connect to the samba share using the owner's username & password.

I *~think~* what you need is to chmod the permission on the folder/files to octal 0744 or maybe 0755 if users connecting to the share need to execute things stored there (the latter sounds dangerous to me!).

I'm a permissions newb so please wait for further clarification from those more knowledgable :D All I know is filesystem permissions will always trump samba permissions.

---

### Post by j_kubik on 2011-11-04
What i wantet to achieve is to have samba use X user credencials (guest account = X), and therefore gain filesystem-access to directory, and then map user X as guest ("guest account" command again :)), therefore granting access for remote user on samba acces check level.

Now I noted that "guest account" is global command, so I cannot use it for single share - I guess filesystem permissions are the only way to go then.

---

