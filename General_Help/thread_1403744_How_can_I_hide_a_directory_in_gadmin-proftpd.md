---
title: "How can I hide a directory in gadmin-proftpd"
date: 2010-02-10
forum: General Help
---

### Post by Eugene_Bondarenko on 2010-02-10
Hi, 

I've installed gadmin-proftpd and used the graphical interface to share a folder via FTP. The folder is */home/eugene/.MOUNT*
This folder is the starting folder for the FTP user (julia).
The folder has many sub-folders and I want to hide some of them and prevent user from accessing them. Below are the configs for the FTP user:
```

<Anonymous /home/eugene/.MOUNT>
User juliab
Group nobody
AnonRequirePassword on
MaxClients 5 "The server is full, hosting %m users"
DisplayLogin welcome.msg
<Limit LOGIN>
Allow from all
Deny from all
</Limit>
<Limit LIST NLST  PWD XPWD  CWD XCWD  CDUP XCUP >
 AllowAll
</Limit>
<Limit STOR STOU  APPE  RETR  RNFR RNTO  DELE  MKD XMKD SITE_MKDIR  RMD XRMD SITE_RMDIR  SITE  SITE_CHMOD  SITE_CHGRP  MTDM  SIZE  STAT >
 DenyAll
</Limit>
<Directory /home/eugene/.MOUNT/.Trash-1000>
<Limit NOTHING >
 AllowAll
</Limit>
<Limit LIST NLST  STOR STOU  APPE  RETR  RNFR RNTO  DELE  MKD XMKD SITE_MKDIR  RMD XRMD SITE_RMDIR  SITE  SITE_CHMOD  SITE_CHGRP  MTDM  PWD XPWD  SIZE  STAT  CWD XCWD  CDUP XCUP >
 DenyAll
</Limit>
</Directory>
</Anonymous>

```
Here I tried to give minimal permissions for the general and main folder */home/eugene/.MOUNT* to allow user navigating in it. Then I tried to hide */home/eugene/.MOUNT/.Trash-1000* by removing all permissions in the gadmin-proftpd however this doesn't produce the expected result. FTP user can still browse into this folder and list its contents and that's the main problem. The next step I am going to do is to grant download, upload and other permissions for folders like */home/eugene/.MOUNT/sdb5/movies* currently I can't resolve the problem with "secret" folders that I need to hide.

Am I doing something wrong? Or should I handle such tasks using system permissions?

---

### Post by Eugene_Bondarenko on 2010-02-12
*bump*

---

