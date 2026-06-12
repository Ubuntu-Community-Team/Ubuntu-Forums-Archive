---
title: "Share entire hard drive via FTP"
date: 2011-07-19
forum: General Help
---

### Post by conradin on 2011-07-19
Hi Everyone,
I have a hard drive with 10 partitions, 4 primary, 6 locgical. I would like to share the entire hard drive via a file server. The har drive is a seprate disk from my main operating system hard drive. I think that means I cant use links? How can I set this up?

---

### Post by 2F4U on 2011-07-20
What kind of sharing do you intend and what operating systems should be able to connect to that hard drive? Is this hdd running in a computer or standalone? There are several possibilities to setup a file server, e.g. ssh, ftp, sftp, nfs, samba, etc., depending on what you want to do.

---

### Post by conradin on 2011-07-20
The hard drive is formated in ext3, and im granting read only access to it via FTP. Im running ubuntu server.

---

### Post by 2F4U on 2011-07-20
Still not sure if I understand you. You can install ftp server software on your server and this would listen to incoming ftp client requests. However, ftp is considered insecure, so I think it is not installed by default. There are several ftp server available, for example proftpd or vsftpd.

---

