---
title: "error while installing qt4"
date: 2010-04-29
forum: General Help
---

### Post by anurag18 on 2010-04-29
Hi all;
I am trying to install qt4 on my ubuntu machine by executing 
 
sudo apt-get install qt4-designer
 
but i am getting following error
 
Reading package lists... Done
Building dependency tree 
Reading state information... Done
The following packages were automatically installed and are no longer required:
libgcj8-1 libgcj-bc libgcj8-jar gij-4.2 gcj-4.2-base libgcj-common
libgcj8-1-awt fastjar
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
libkadm55 libkrb5-dev libkrb53 libmysqlclient15off libpq-dev libqt4-dev
libqt4-qt3support libqt4-sql mysql-common
Suggested packages:
krb5-doc krb5-user postgresql-doc-8.3 qt4-doc
Recommended packages:
qt4-dev-tools
The following NEW packages will be installed:
libkadm55 libkrb5-dev libmysqlclient15off libpq-dev libqt4-dev
libqt4-qt3support libqt4-sql mysql-common qt4-designer
The following packages will be upgraded:
libkrb53
1 upgraded, 9 newly installed, 0 to remove and 146 not upgraded.
Need to get 2593kB/9581kB of archives.
After this operation, 35.0MB of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
libkrb53 libkadm55 mysql-common libmysqlclient15off libkrb5-dev libpq-dev
libqt4-sql libqt4-qt3support libqt4-dev qt4-designer
Install these packages without verification [y/N]? y
Err [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) hardy-updates/main libkrb53 1.6.dfsg.3~beta1-2ubuntu1.3
Connection failed
Err [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main libkrb53 1.6.dfsg.3~beta1-2ubuntu1.3
Connection failed [IP: 91.189.88.31 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main libkadm55 1.6.dfsg.3~beta1-2ubuntu1.3
Connection failed [IP: 91.189.88.31 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main mysql-common 5.0.51a-3ubuntu5.4
Connection failed [IP: 91.189.88.31 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main libmysqlclient15off 5.0.51a-3ubuntu5.4
Connection failed [IP: 91.189.88.31 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main libkrb5-dev 1.6.dfsg.3~beta1-2ubuntu1.3
Connection failed [IP: 91.189.88.31 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/k/krb5/libkrb53_1.6.dfsg.3~beta1-2ubuntu1.3_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/k/krb5/libkrb53_1.6.dfsg.3~beta1-2ubuntu1.3_i386.deb) Connection failed [IP: 91.189.88.31 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/k/krb5/libkadm55_1.6.dfsg.3~beta1-2ubuntu1.3_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/k/krb5/libkadm55_1.6.dfsg.3~beta1-2ubuntu1.3_i386.deb) Connection failed [IP: 91.189.88.31 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/m/mysql-dfsg-5.0/mysql-common_5.0.51a-3ubuntu5.4_all.deb](http://security.ubuntu.com/ubuntu/pool/main/m/mysql-dfsg-5.0/mysql-common_5.0.51a-3ubuntu5.4_all.deb) Connection failed [IP: 91.189.88.31 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/m/mysql-dfsg-5.0/libmysqlclient15off_5.0.51a-3ubuntu5.4_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/m/mysql-dfsg-5.0/libmysqlclient15off_5.0.51a-3ubuntu5.4_i386.deb) Connection failed [IP: 91.189.88.31 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/k/krb5/libkrb5-dev_1.6.dfsg.3~beta1-2ubuntu1.3_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/k/krb5/libkrb5-dev_1.6.dfsg.3~beta1-2ubuntu1.3_i386.deb) Connection failed [IP: 91.189.88.31 80]
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
 
 
how to resolve this error ?Please help

---

### Post by klemes on 2010-04-29
I see you are using Hardy.If you are not using Hardy 8.04.4 the rest of the hardy releases(.1,.2,.3) have been moved to the old-releases.ubuntu.com repository.You can see which version you are using by lsb_release-r and either try to perform  a dist-upgrade to the latest hardy heron version(if it's still possible) or change your software sources in /etc/apt/sources.list accordingly to old-releases.ubuntu.com hardy etc.and perform an apt-get update.

---

