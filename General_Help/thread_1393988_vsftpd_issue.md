---
title: "vsftpd issue"
date: 2010-01-30
forum: General Help
---

### Post by linkally on 2010-01-30
I installed 2 version Ubuntu, one is Ubuntu 9.04 Jaunty Alestic, login user is root, and Ubuntu 9.10 Karmic Alestic, login user is ubuntu, both only install vsftpd, set the same config, all allow anonymous upload, and passive mode as below: [B]
  pasv_enable=yes 
  pasv_port_min=10000 
  pasv_port_max=10024 
  pasv_address= xxx(my server ip) 
   
  anon_root=/var/ftp 
   
[/B]  And I mkdir "upload" bolow ftp. 
  But the first Ubuntu I can upload corrently, the second says:
-----------------------------------
......
Response:    200 Switching to Binary mode.
Command:    PASV
Response:    500 OOPS: child died
Command:    PORT xxx,xxx,xxx,xxx,14,166
Error:    Connection closed by server
Error:    Failed to retrieve directory listing
......
----------------------------------
I am so confused about this problem, maybe caused by system login user ID?

Thanks
Mike

---

### Post by adeelm on 2010-02-08
[SIZE=3]Simply comment the line [/SIZE][SIZE=4][SIZE=3]from this

[/SIZE][/SIZE][SIZE=4] secure_chroot_dir=/var/run/vsftpd[/SIZE]

[SIZE=3]to this[/SIZE]

[SIZE=4]# secure_chroot_dir=/var/run/vsftpd[/SIZE]
[SIZE=4]

Adeel
[/SIZE]

---

