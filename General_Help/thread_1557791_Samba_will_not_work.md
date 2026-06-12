---
title: "Samba will not work"
date: 2010-08-21
forum: General Help
---

### Post by 73ckn797 on 2010-08-21
Hope this helps someone.

During a recent update I started receiving the following error messages. I have un-installed Samba and related components and when trying to reinstall this message also comes up. 

```
E: samba-common: subprocess installed post-installation script returned error exit status 1
E: samba-common-bin: dependency problems - leaving unconfigured
E: samba: dependency problems - leaving unconfigured
E: smbclient: dependency problems - leaving unconfigured
E: smbfs: dependency problems - leaving unconfigured
E: system-config-samba: dependency problems - leaving unconfigured
E: winbind: dependency problems - leaving unconfigured
```
I ran the following:
```
sudo dpkg --configure -a

Setting up samba-common (2:3.4.7~dfsg-1ubuntu3.1) ...
Not replacing deleted config file /etc/samba/smb.conf
Install/upgrade will fail. To recover, please try:
  sudo cp /usr/share/samba/smb.conf /etc/samba/smb.conf
  sudo dpkg --configure -a
dpkg: error processing samba-common (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of smbclient:
 smbclient depends on samba-common (= 2:3.4.7~dfsg-1ubuntu3.1); however:
  Package samba-common is not configured yet.
dpkg: error processing smbclient (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of samba-common-bin:
 samba-common-bin depends on samba-common (>= 2:3.4.0~pre1-2); however:
  Package samba-common is not configured yet.
dpkg: error processing samba-common-bin (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of samba:
 samba depends on samba-common (= 2:3.4.7~dfsg-1ubuntu3.1); however:
  Package samba-common is not configured yet.
 samba depends on samba-common-bin; however:
  Package samba-common-bin is not configured yet.
dpkg: error processing samba (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of system-config-samba:
 system-config-samba depends on samba; however:
  Package samba is not configured yet.
dpkg: error processing system-config-samba (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of winbind:
 winbind depends on samba-common (= 2:3.4.7~dfsg-1ubuntu3.1); however:
  Package samba-common is not configured yet.
dpkg: error processing winbind (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of smbfs:
 smbfs depends on samba-common (= 2:3.4.7~dfsg-1ubuntu3.1); however:
  Package samba-common is not configured yet.
dpkg: error processing smbfs (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 samba-common
 smbclient
 samba-common-bin
 samba
 system-config-samba
 winbind
 smbfs
```Reading the results I followed the recommendation for terminal:
```
sudo cp /usr/share/samba/smb.conf /etc/samba/smb.conf
sudo dpkg --configure -a
```This corrected the error messages and all appears to be fixed.

---

### Post by 73ckn797 on 2010-08-24
I spoke too soon. Samba installed but will not work. The desktop computer I am using is running 10.04 but is not seen by another laptop and desktop. The laptop is using 10.04 and the other desktop is using 9.04. I can access the other desktop from the laptop and that desktop can access the laptop but my main desktop is not recognized. Tha main desktop can see the other computers. I have purged the samba installtion on the main desktop and shut it down.

Any suggestions?

---

