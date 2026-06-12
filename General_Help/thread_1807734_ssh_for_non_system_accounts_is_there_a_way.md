---
title: "ssh for non system accounts? is there a way?"
date: 2011-07-19
forum: General Help
---

### Post by ingramproductions on 2011-07-19
I currently have an ftp server setup using Ubuntu 10.04 and pureftpd with mysql as the backend. All the ftp users are "virual users" that are stored in mysql. I want my existing users to be able to use scp to transfer files instead of ftp. As far as I know, you can only use ssh/scp if you have a system account. All of my virtual users use the same system account of "ftpuser".

Is it even possible for me to setup the users with scp access, even though they don't have an actual system account? I really don't want to setup system accounts for each user. I have a lot of ftp users and I plan on expanding that number, so adding system accounts isn't ideal, plus I feel like that will bring new security issues (researching chroot for ssh and how to lock down ssh).

---

### Post by Jguy on 2011-07-19
I believe you would set their shell to /bin/false, which will not allow them to login via ssh.

---

### Post by blind2314 on 2011-07-19
> **ingramproductions said:**
> I currently have an ftp server setup using Ubuntu 10.04 and pureftpd with mysql as the backend. All the ftp users are "virual users" that are stored in mysql. I want my existing users to be able to use scp to transfer files instead of ftp. As far as I know, you can only use ssh/scp if you have a system account. All of my virtual users use the same system account of "ftpuser".
 
Is it even possible for me to setup the users with scp access, even though they don't have an actual system account? I really don't want to setup system accounts for each user. I have a lot of ftp users and I plan on expanding that number, so adding system accounts isn't ideal, plus I feel like that will bring new security issues (researching chroot for ssh and how to lock down ssh).
 
 
Why not use SFTP? You can allow users to share an account, and you'll have the security it seems you're after.

---

### Post by ingramproductions on 2011-07-24
I decided to not mess with it and I went with ftps.

---

