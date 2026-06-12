---
title: "Mount a FTP Folder"
date: 2009-10-16
forum: General Help
---

### Post by Laire on 2009-10-16
Hello,

I try to mount a FTP Folder. Not only "Connect Server" .

My target is, that PCs in my network have access to the Folder, but only when they are in my network. When they leave it, there is no access. 

My idea was to mount the FTP on my homeserver and give acces over samba. With this line in the fstab file I mount it:

```
curlftpfs#<user>:<password>@<ftpserver> /media/ftp_markus fuse rw,allow_other,noauto,user 0 0
```

It mount the FTP Folder, but the problem is, that I cant make changes. When I open a file on the FTP and edit it, I can't save the file.

---

### Post by MaindotC on 2009-10-16
Just pull the file via FTP, edit it on your machine, and then FTP it back to overwrite the previous file.  I have the same problem accessing campus windows-based shares at my college because they are a windoze environment.

---

### Post by Laire on 2009-10-16
Sorry, but I search a way to edit the files directly on the server. To copy every two minutes file from on location to the other i not OK

---

### Post by Laire on 2009-10-17
Nobody an idea...

---

### Post by StuartN on 2009-10-17
> **Laire said:**
> ```
curlftpfs#<user>:<password>@<ftpserver> /media/ftp_markus fuse rw,allow_other,noauto,user 0 0
```

I do not know where you entering this, but adding uid=<yourusername>,gid=<yourgroupname> to the options might work.

Edit: (I have not noticed any problem with FTP - I connect to my website using an FTP bookmark in Nautilus and I have read/write access with all applications).

---

