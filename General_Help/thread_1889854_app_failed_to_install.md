---
title: "app failed to install"
date: 2011-12-02
forum: General Help
---

### Post by 4x40ranger on 2011-12-02
[FONT=monospace]I have zorin-os5 baised from ubuntu 11.04 I tried to install a game and got a message that said I needed to repair a broken packet and got this error message. any help is appreciated. i'm new to linux.

installArchives() failed: perl: warning: Setting locale failed. 
perl: warning: Please check that your locale settings: 
    LANGUAGE = (unset), 
    LC_ALL = (unset), 
    LANG = "None.None" 
    are supported and installed on your system. 
perl: warning: Falling back to the standard locale ("C"). 
locale: Cannot set LC_CTYPE to default locale: No such file or directory 
locale: Cannot set LC_MESSAGES to default locale: No such file or directory 
locale: Cannot set LC_ALL to default locale: No such file or directory 
perl: warning: Setting locale failed. 
perl: warning: Please check that your locale settings: 
    LANGUAGE = (unset), 
    LC_ALL = (unset), 
    LANG = "None.None" 
    are supported and installed on your system. 
perl: warning: Falling back to the standard locale ("C"). 
locale: Cannot set LC_CTYPE to default locale: No such file or directory 
locale: Cannot set LC_MESSAGES to default locale: No such file or directory 
locale: Cannot set LC_ALL to default locale: No such file or directory 
perl: warning: Setting locale failed. 
perl: warning: Please check that your locale settings: 
    LANGUAGE = (unset), 
    LC_ALL = (unset), 
    LANG = "None.None" 
    are supported and installed on your system. 
perl: warning: Falling back to the standard locale ("C"). 
locale: Cannot set LC_CTYPE to default locale: No such file or directory 
locale: Cannot set LC_MESSAGES to default locale: No such file or directory 
locale: Cannot set LC_ALL to default locale: No such file or directory 
(Reading database ...  (Reading database ... 5% (Reading database ... 10% (Reading database ... 15% (Reading database ... 20% (Reading database ... 25% (Reading database ... 30% (Reading database ... 35% (Reading database ... 40% (Reading database ... 45% (Reading database ... 50% (Reading database ... 55% (Reading database ... 60% (Reading database ... 65% (Reading database ... 70% (Reading database ... 75% (Reading database ... 80% (Reading database ... 85% (Reading database ... 90% (Reading database ... 95% (Reading database ... 100% (Reading database ... 176504 files and directories currently installed.) 
Unpacking assaultcube-data (from .../assaultcube-data_1.0.4+repack1-1_all.deb) ... 
dpkg-deb (subprocess): data: internal gzip read error: '<fd:0>: data error' 
dpkg-deb: error: subprocess <decompress> returned error exit status 2 
dpkg: error processing /var/cache/apt/archives/assaultcube-data_1.0.4+repack1-1_all.deb (--unpack): 
 subprocess dpkg-deb --fsys-tarfile returned error exit status 2 
No apport report written because MaxReports is reached already
Errors were encountered while processing: 
 /var/cache/apt/archives/assaultcube-data_1.0.4+repack1-1_all.deb 
dpkg: dependency problems prevent configuration of assaultcube: 
 assaultcube depends on assaultcube-data (>= 1.0.4+repack1); however: 
  Package assaultcube-data is not installed. 
dpkg: error processing assaultcube (--configure): 
 dependency problems - leaving unconfigured 

[/FONT]

---

### Post by BC59 on 2011-12-02
Run from a terminal

```
sudo dpkg --configure -a
sudo apt-get -f install
```

---

