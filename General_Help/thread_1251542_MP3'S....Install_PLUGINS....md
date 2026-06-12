---
title: "MP3'S....Install PLUGINS..."
date: 2009-08-27
forum: General Help
---

### Post by MistaMista on 2009-08-27
I am trying to play mp3's on my ubuntu os...and when i try to install the needed plugins i keep gettin this msg.....E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

---

### Post by jerome1232 on 2009-08-27
> **MistaMista said:**
> I am trying to play mp3's on my ubuntu os...and when i try to install the needed plugins i keep gettin this msg.....E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

Have you tried running that command the error message recommended?

---

### Post by scouser73 on 2009-08-27
Go to **Terminal**, copy & paste this command:  **sudo dpkg --configure -a**

---

### Post by MistaMista on 2009-08-27
i ran the command and got this......Setting up java-common (0.30ubuntu4) ...

Processing triggers for man-db ...
Processing triggers for doc-base ...
Processing 2 added doc-base file(s)...
Registering documents with scrollkeeper...
Setting up bcm43xx-fwcutter (1:006-1) ...
--2009-08-27 16:39:07--  [http://boredklink.googlepages.com/wl_apsta.o](http://boredklink.googlepages.com/wl_apsta.o)
Resolving boredklink.googlepages.com... 74.125.159.118, 74.125.159.133
Connecting to boredklink.googlepages.com|74.125.159.118|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
2009-08-27 16:39:07 ERROR 404: Not Found.

dpkg: error processing bcm43xx-fwcutter (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 bcm43xx-fwcutter

---

