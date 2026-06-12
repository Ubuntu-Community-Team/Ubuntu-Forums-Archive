---
title: "VSFTPD Users Problems"
date: 2009-08-11
forum: General Help
---

### Post by jfreak53 on 2009-08-11
Ok I have installed VSFTPD and got it working.  But no where can I find directions for exactly what I need to do.  I need to be able to add users and give them access to my apache www dir.  Some of the created users need access to the root www dir and some I need to create their own dirs and only give them access to it.  My vsftpd.conf file is default from install I only disabled anon access and added where local users and host can log in for testing purposes.

So I need directions on how to add users like that and setup the ftp system for this use.  My apache www dir is /var/www and owned by www-data and the group I have giving full rights to.  What's better system users or virtual users.  I would think virtul would be better since I wouldn't have to be adding users to the system.  Less security risk.  I already installed the package libpam-pwdfile trying to make virtual users work through a tut, but the tut had me totally confused.  So I turned everything back to install config minus what I already told you and left package installed.

Thanks for any help you can give me.  My ubuntu system is 9.04

---

