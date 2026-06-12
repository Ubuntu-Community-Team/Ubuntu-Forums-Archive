---
title: "Unable to install anything with software center"
date: 2012-02-09
forum: General Help
---

### Post by agoodliffe on 2012-02-09
Hello I think I am having the same problem. I just replaced my old laptop which had  Xubuntu 9.4 with a new one and installed Ubuntu 11.10. My knowledge has always been rather limited when it comes to fine tuning my OS. After installing in dual boot with my Windows I am unable to install any new software from the Ubuntu Software Centre. 
I  tried sudo apt-get update and sudo apt-get upgrade and still the problem persists.
I have tried downloading and installing Skype and even Synaptic from Ubuntu Software Centre and here is the response the machine gives me. Any recommendations? 
[HTML]installArchives() failed: Selecting previously deselected package libept1.

(Reading database ... 

(Reading database ... 5%

(Reading database ... 10%

(Reading database ... 15%

(Reading database ... 20%

(Reading database ... 25%

(Reading database ... 30%

(Reading database ... 35%

(Reading database ... 40%

(Reading database ... 45%

(Reading database ... 50%

(Reading database ... 55%

(Reading database ... 60%

(Reading database ... 65%

(Reading database ... 70%

(Reading database ... 75%

(Reading database ... 80%

(Reading database ... 85%

(Reading database ... 90%

(Reading database ... 95%

(Reading database ... 100%

(Reading database ... 128583 files and directories currently installed.)

Unpacking libept1 (from .../libept1_1.0.5build1_amd64.deb) ...

Selecting previously deselected package synaptic.

Unpacking synaptic (from .../synaptic_0.75.2ubuntu8_amd64.deb) ...

Processing triggers for hicolor-icon-theme ...

Processing triggers for gnome-menus ...

Processing triggers for desktop-file-utils ...

Processing triggers for bamfdaemon ...

Rebuilding /usr/share/applications/bamf.index...

Processing triggers for man-db ...

Setting up flashplugin-downloader:i386 (11.0.1.152ubuntu1) ...

Downloading...

--2012-02-09 19:13:11--  http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_11.0.1.152.orig.tar.gz

Resolving archive.canonical.com... 91.189.88.33

Connecting to archive.canonical.com|91.189.88.33|:80... connected.

HTTP request sent, awaiting response... 404 Not Found

2012-02-09 19:13:11 ERROR 404: Not Found.



download failed

The Flash plugin is NOT installed.

dpkg: error processing flashplugin-downloader:i386 (--configure):

 subprocess installed post-installation script returned error exit status 1

dpkg: dependency problems prevent configuration of flashplugin-installer:

 flashplugin-installer depends on flashplugin-downloader (>= 11.0.1.152ubuntu1); however:

  Package flashplugin-downloader is not installed.

  Package flashplugin-downloader:i386 is not configured yet.

dpkg: error processing flashplugin-installer (--configure):

 dependency problems - leaving unconfigured

No apport report written because the error message indicates its a followup error from a previous failure.

Setting up libept1 (1.0.5build1) ...

Setting up synaptic (0.75.2ubuntu8) ...

Processing triggers for libc-bin ...

ldconfig deferred processing now taking place

Errors were encountered while processing:

 flashplugin-downloader:i386

 flashplugin-installer

Error in function: 

SystemError: E:Sub-process /usr/bin/dpkg returned an error code (1)

Setting up flashplugin-downloader:i386 (11.0.1.152ubuntu1) ...

Downloading...

--2012-02-09 19:13:12--  http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_11.0.1.152.orig.tar.gz
	
Resolving archive.canonical.com... 91.189.88.33

Connecting to archive.canonical.com|91.189.88.33|:80... connected.

HTTP request sent, awaiting response... 404 Not Found

2012-02-09 19:13:13 ERROR 404: Not Found.



download failed

The Flash plugin is NOT installed.

dpkg: error processing flashplugin-downloader:i386 (--configure):

 subprocess installed post-installation script returned error exit status 1

dpkg: dependency problems prevent configuration of flashplugin-installer:

 flashplugin-installer depends on flashplugin-downloader (>= 11.0.1.152ubuntu1); however:

  Package flashplugin-downloader is not installed.

  Package flashplugin-downloader:i386 is not configured yet.

dpkg: error processing flashplugin-installer (--configure):

 dependency problems - leaving unconfigured

Errors were encountered while processing:
[/HTML]

---

### Post by Stu15 on 2012-02-09
Seems perculiar, are you behind a proxy?

Maybe try this in terminal, seen someone with the same problem, see if you get anything back from typing this.

sudo apt-get install flashplugin-installer

Then if it installs the flash plugin it may then install updates and apps.

Also you could try updating from Update manager, or if you have a disk of ubuntu 11.10 you could try installing packages from that (Automatically asks when inserted) It may fix anything thats missing.

---

### Post by hansdown on 2012-02-09
Good advice, Stu15. :D

agoodliffe, also try

```
sudo apt-get update 
```

---

### Post by Cookieh on 2012-02-11
Well, firstly, looks like you are getting 404 error which would actually mean that either your database is out of date or there is a malfunction in your system.

What I did to get out of this error is do this

```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get upgrade -y
```

This has helped me to update my database and get rid of the 404
HTTP request sent, awaiting response... 404 Not Found

---

