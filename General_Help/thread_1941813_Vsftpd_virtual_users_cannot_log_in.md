---
title: "Vsftpd virtual users cannot log in"
date: 2012-03-16
forum: General Help
---

### Post by Poma on 2012-03-16
vsftpd wont let me to log in. Here is my vsftpd.conf:

```
listen=YES
anonymous_enable=NO
local_enable=YES
virtual_use_local_privs=YES
write_enable=YES
connect_from_port_20=YES
secure_chroot_dir=/var/run/vsftpd
pam_service_name=vsftpd
guest_enable=YES
user_sub_token=$USER
local_root=/var/test/$USER
chroot_local_user=YES
hide_ids=YES
```

and pam file:

```
auth    required pam_pwdfile.so pwdfile /etc/vsftpd/passwd
account required pam_permit.so
```

When I try to log in:

```
root@ubuntu:/# ftp 127.0.0.1
Connected to 127.0.0.1.
220 (vsFTPd 2.2.2)
Name (127.0.0.1:poma): bob
331 Please specify the password.
Password:
530 Login incorrect.
Login failed.
ftp>
```

How to find out what's the problem?

---

