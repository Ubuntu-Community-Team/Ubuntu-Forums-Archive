---
title: "FTP Server setup"
date: 2010-12-09
forum: General Help
---

### Post by spindler on 2010-12-09
I am attempting to install/set up an FTP server on Ubuntu 10.4.

I took a look at [https://help.ubuntu.com/community/FtpServer](https://help.ubuntu.com/community/FtpServer)


I want to set up `virtual users with MySQL`  I could not find PureFTPd  in the UBUNTU SOFTWARE CENTER but I did find Pure Admin.   Is this the same thing?


Does anyone know how to set up an FTP server so I can log in to my website  folder and gain access to mysql?

Is there a detailed document describing everything I need to do?

Thanks,
  
Spindler

---

### Post by drdos2006 on 2010-12-09
Have a look at vsftp, it may be a lot easier to set up than PureFTP.

regards

---

### Post by elliotbeken on 2010-12-09
Yeh i agree with drdos2006 vsftpd is simple and at the same time secure, also i am sure you can use it with a database ...

good luck

---

### Post by lukeiamyourfather on 2010-12-09
> **spindler said:**
> 
I want to set up `virtual users with MySQL`  I could not find PureFTPd  in the UBUNTU SOFTWARE CENTER but I did find Pure Admin.   Is this the same thing?


I'm not familar with those packages, though the software center has select packages that are popular. For a complete list of packages use apt-get/apt-cache, aptitude or similar.

---

### Post by spindler on 2010-12-14
Yes....I have tried many different FTP server packages.  None of them seem to install correctly.  I cannot find a configuration process or anything.

I have decided to focus my attention on installing PureFTPd  following the instructions provided.   The installation is from a FreeBSD point of view and not linux so I could use a little help.

I first took a look at this site.   [https://help.ubuntu.com/community/FtpServer](https://help.ubuntu.com/community/FtpServer)  It provides basic information about installing Pure- FTPd and points to the step by step instructions provided by  [http://machiel.generaal.net/index.php?subject=user_manager_pureftpd](http://machiel.generaal.net/index.php?subject=user_manager_pureftpd) 

I have analyzed my hardware set up and have enough information to create the pure-ftpd.conf  and pureftpd-mysql.conf files.

These files do not exists on my system and they are not included in the PureFTPd package .  I am not sure what to do.  The instructions say.... The location of both files is depending on your operation system, for FreeBSD for example this is /usr/local/etc/. When you can't find those files you probably still have to copy the two example files of Pure-ftpd called:  pure-ftpd.conf.sample  and  pure-ftpf-mysql.conf.sample.

1.  These two files are not included in the package.....Any idea where I can get these files ?

2.  Do you know where I need to put the files in the Ubuntu 10.4 Linux server?

---

