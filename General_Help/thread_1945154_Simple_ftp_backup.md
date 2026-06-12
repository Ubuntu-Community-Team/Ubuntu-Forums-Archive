---
title: "Simple ftp backup"
date: 2012-03-22
forum: General Help
---

### Post by psgill on 2012-03-22
Hello everyone,

I am looking to setup a simple backup of compressed files via ftp.
I used curlftpfs to mount the remote server's ftp directory.

If I place something in the mounted directory it doesn't seem like it is being written on the ftp server.
Also, I am not able to see the existing contents on ftp which tells me either I have configured something wrong or the fact that curlftpfs is abandoned and has compatibility issues with newer software.

I did the simple install of curlftpfs and added the following to my /etc/fstab

```

curlftpfs#user:pw@10.10.10.10:1313 /mnt/ftpbackup fuse rw,all_other,uid=1001 0 0

```

There is no error while mounting but no transfers take place!

Can anyone suggest me an alternative program or even a script to make the backup from the linux box to the ftp server running on another windows system?

Thanks.

---

### Post by nothingspecial on 2012-03-22
*Thread moved to **General Help**.*

@psgill If you post in tutorials and tips no one can see your question until one of the staff approves it.

---

### Post by jonobr on 2012-03-22
Hello


I would recommend using [rsync]("https://help.ubuntu.com/community/rsync") as its ideal for this.

You could also use secure copy (SCP) but give rsync a look first, 
if you dont like it Ill give more info on scp

For your ftp issue if you want to use that I would recommend just manually trying to move the compressed file via ftp and see if it throws any errors in the way of permissions etc.

---

