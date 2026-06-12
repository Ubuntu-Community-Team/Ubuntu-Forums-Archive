---
title: "Package Operation Failed"
date: 2011-12-30
forum: General Help
---

### Post by jazzrazor on 2011-12-30
keep on getting the following error when I try to download software:

[quote]"The installation or removal of the software package failed."/quote]


```
installArchives() failed: (Reading database ...  (Reading database ... 5% (Reading database ... 10% (Reading database ... 15% (Reading database ... 20% (Reading database ... 25% (Reading database ... 30% (Reading database ... 35% (Reading database ... 40% (Reading database ... 45% (Reading database ... 50% (Reading database ... 55% (Reading database ... 60% (Reading database ... 65% (Reading database ... 70% (Reading database ... 75% (Reading database ... 80% (Reading database ... 85% (Reading database ... 90% (Reading database ... 95% (Reading database ... 100% (Reading database ... 125085 files and directories currently installed.) 
Removing flashplugin-installer ... 
Setting up flashplugin-downloader:i386 (11.0.1.152ubuntu1) ... 
Downloading... 
--2011-12-31 09:57:52--  [http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_11.0.1.152.orig.tar.gz](http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_11.0.1.152.orig.tar.gz) 
Resolving archive.canonical.com... 91.189.88.33 
Connecting to archive.canonical.com|91.189.88.33|:80... connected. 
HTTP request sent, awaiting response... 404 Not Found 
2011-12-31 09:57:53 ERROR 404: Not Found. 

download failed 
The Flash plugin is NOT installed. 
dpkg: error processing flashplugin-downloader:i386 (--configure): 
 subprocess installed post-installation script returned error exit status 1 
Errors were encountered while processing: 
 flashplugin-downloader:i386 
Error in function:  
SystemError: E:Sub-process /usr/bin/dpkg returned an error code (1) 
Setting up flashplugin-downloader:i386 (11.0.1.152ubuntu1) ... 
Downloading... 
--2011-12-31 09:57:54--  [http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_11.0.1.152.orig.tar.gz](http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_11.0.1.152.orig.tar.gz) 
Resolving archive.canonical.com... 91.189.88.33 
Connecting to archive.canonical.com|91.189.88.33|:80... connected. 
HTTP request sent, awaiting response... 404 Not Found 
2011-12-31 09:57:55 ERROR 404: Not Found. 

download failed 
The Flash plugin is NOT installed. 
dpkg: error processing flashplugin-downloader:i386 (--configure): 
 subprocess installed post-installation script returned error exit status 1 
Errors were encountered while processing: 

```

i tried some commands :-

these command i seen in this forum ..but it doesn't  work

command 1: ```
sudo apt-get update 
```
command 2:- ```
sudo dpkg --configure -a
```


When i run  command 3 it say:

```
sudo apt-get purge synaptics-dkms 


error:-  Unable to locate package synaptics-dkms
     


```
 

i need help .....plz help me

---

### Post by 2F4U on 2011-12-31
What version of Ubuntu are you using?

Can you enter the following commands in a terminal and post the output:

```

sudo apt-get update
sudo apt-get dist-upgrade

```

---

### Post by thedarkdonut on 2011-12-31
Is this happening with all software?  What command are you using to install the software?

---

### Post by spacecheck on 2011-12-31
The package you are trying to install (adobe-flashplugin_11.0.1.152.orig.tar.gz) does not exist in that version at that location ([http://archive.canonical.com/pool/partner/a/adobe-flashplugin/](http://archive.canonical.com/pool/partner/a/adobe-flashplugin/)). Perhaps you could try a different, more recent version? Several appear to be available there.  Good luck!

---

