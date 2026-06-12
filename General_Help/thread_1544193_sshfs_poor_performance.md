---
title: "sshfs poor performance"
date: 2010-08-02
forum: General Help
---

### Post by drukh on 2010-08-02
Hi,

I am using sshfs mount within a LAN with default parameters.
It works terribly slow for both writing large files (MBs) and referencing (like du -hs) a directory with a lots of small files (like thousands).

Any hints for the mount options that may improve this?

Thanks,

  Evgeny

---

### Post by OriginalName on 2010-08-04
I'm guessing sshfs is a tunneled filesystem over ssh?

I use sftp & it gets significantly slower file transfers than straight ftp... I think the speed is down to the encrypted nature of the connection... everything that is sent / received has to be encrypted / decrypted so the speed will be limited as much by CPU power as network speed.

On 100 MB/s LAN I get FTP transfer of around 10MB/s, SFTP at around 1MB/s or less!

---

### Post by aeiah on 2010-08-04
i get 5mb/s on sftp and 11mb/s on ftp through a 100mbit lan, for the record. is there a reason why you're using sshfs on a LAN instead of ftpfs, samba or nfs?

---

