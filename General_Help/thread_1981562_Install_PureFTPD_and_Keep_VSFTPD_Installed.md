---
title: "Install PureFTPD and Keep VSFTPD Installed"
date: 2012-05-17
forum: General Help
---

### Post by own3mall on 2012-05-17
Hi All,

Is there any way I can install PureFTPD and keep VSFTPD from being removed?  I need VSFTPD for my web hosting control panel, and I need PureFTPD for my game server management software, as VSFTPD is not supported through the gaming package.

My plan is to run PureFTPD on a different port.  This should not interfere with VSFTPD, correct?  How would I go about installing PureFTPD while keeping VSFTPD?  

When I try to install it using the following, it tells me that the package VSFTPD will be removed.

```

:~$ sudo apt-get install pure-ftpd
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libdmraid1.0.0.rc16 ubufox python-pyicu libparted0 libdebian-installer4
  cryptsetup rdate bogl-bterm ylmfox libdebconfclient0 dmraid
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  openbsd-inetd pure-ftpd-common
The following packages will be REMOVED:
  vsftpd
The following NEW packages will be installed:
  openbsd-inetd pure-ftpd pure-ftpd-common
0 upgraded, 3 newly installed, 1 to remove and 0 not upgraded.
Need to get 372kB of archives.
After this operation, 631kB of additional disk space will be used.
Do you want to continue [Y/n]? 


```

---

### Post by own3mall on 2012-05-17
Anyone?

---

