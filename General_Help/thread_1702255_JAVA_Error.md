---
title: "JAVA Error"
date: 2011-03-07
forum: General Help
---

### Post by shibby4555 on 2011-03-07
Just installed Java so I use ADrive uploader. Uploaded one file then after that I got this error message from JAVA. Any idea to remedy this?
Thanks in advance,
-shibby






Java Plug-in 1.6.0_24
Using JRE version 1.6.0_24-b07 Java HotSpot(TM) 64-Bit Server VM
User home directory = /home/shibby
----------------------------------------------------
c:   clear console window
f:   finalize objects on finalization queue
g:   garbage collect
h:   display this help message
l:   dump classloader list
m:   print memory usage
o:   trigger logging
q:   hide console
r:   reload policy configuration
s:   dump system and deployment properties
t:   dump thread list
v:   dump thread stack
x:   clear classloader cache
0-5: set trace level to <n>
----------------------------------------------------


MyUploader Standard Edition version 1.14
© Copyright JavaAtWork B.V. 2005-2010. All rights reserved.


Mar 7, 2011 3:14:10 PM java.util.prefs.FileSystemPreferences$2 run
INFO: Created user preferences directory.
Mar 7, 2011 3:16:06 PM - HTTPUploadTask - upload() - java.net.SocketException: Socket closed
Mar 7, 2011 3:16:48 PM - HTTPUploadTask - upload() - HTTP/1.1 200 OK 

exception: Permission denied: [http://www.adrive.com/java/](http://www.adrive.com/java/).
java.lang.SecurityException: Permission denied: [http://www.adrive.com/java/](http://www.adrive.com/java/)
    at sun.plugin2.applet.Plugin2Manager$AppletExecutionRunnable.run(Plugin2Manager.java:1483)
    at java.lang.Thread.run(Thread.java:662)
Exception: java.lang.SecurityException: Permission denied: [http://www.adrive.com/java/](http://www.adrive.com/java/)
exception: Permission denied: [http://www.adrive.com/java/](http://www.adrive.com/java/).
java.lang.SecurityException: Permission denied: [http://www.adrive.com/java/](http://www.adrive.com/java/)
    at sun.plugin2.applet.Plugin2Manager$AppletExecutionRunnable.run(Plugin2Manager.java:1483)
    at java.lang.Thread.run(Thread.java:662)
Exception: java.lang.SecurityException: Permission denied: [http://www.adrive.com/java/](http://www.adrive.com/java/)

---

### Post by macflav on 2011-04-02
My problem seems a bit simpler, but I can't find a workaround.

```
Java Plug-in 1.6.0_24
Using JRE version 1.6.0_24-b07 Java HotSpot(TM) 64-Bit Server VM
User home directory = /home/macflav
----------------------------------------------------
c:   clear console window
f:   finalize objects on finalization queue
g:   garbage collect
h:   display this help message
l:   dump classloader list
m:   print memory usage
o:   trigger logging
q:   hide console
r:   reload policy configuration
s:   dump system and deployment properties
t:   dump thread list
v:   dump thread stack
x:   clear classloader cache
0-5: set trace level to <n>
----------------------------------------------------


exception: Permission denied: file:/home/macflav/HODCCacesso.serpro.gov.br/Release/.
java.lang.SecurityException: Permission denied: file:/home/macflav/HODCCacesso.serpro.gov.br/Release/
    at sun.plugin2.applet.Plugin2Manager$AppletExecutionRunnable.run(Plugin2Manager.java:1483)
    at java.lang.Thread.run(Thread.java:662)
Exception: java.lang.SecurityException: Permission denied: file:/home/macflav/HODCCacesso.serpro.gov.br/Release/
```
Tried setting folder permissions to "create and delete files", but the error persists. Can't think of anything else.

---

### Post by joshuapurcell on 2011-04-06
Same problem from the looks of it:
```
Java Plug-in 1.6.0_24
Using JRE version 1.6.0_24-b07 Java HotSpot(TM) Server VM
User home directory = /home/joshua

----------------------------------------------------
c:   clear console window
f:   finalize objects on finalization queue
g:   garbage collect
h:   display this help message
l:   dump classloader list
m:   print memory usage
o:   trigger logging
q:   hide console
r:   reload policy configuration
s:   dump system and deployment properties
t:   dump thread list
v:   dump thread stack
x:   clear classloader cache
0-5: set trace level to <n>
----------------------------------------------------

NLS Loader >> Static block - Loading NLS defaults array
NLS Loader >> Static block - attempting to load com.ibm.ers.ersinst.com.ibm.ers.ersinst.exc.ERSInstaller.properties bundle for en_US
NLS Loader >> Static block - nlsBundle was loaded for com.ibm.ers.ersinst.exc.ERSInstaller locale en_US
NLS Loader >> getString() for : OKMSG
NLS Loader >> Static block - getString("OKMSG") = OK
Installer >> Checking permissions - java vendor = SUN MICROSYSTEMS INC.
Installer >> ERS Applet Installer - version 1,0,0,39
Installer >> ZIPFILE = FeLaunch.zip
Installer >> ERS_USEAPPDATA = false
Installer >> ERS_SHARED = true
Installer >> ERS_FORCE = true
Installer >> ERS_JAVA2VERSION = 1.5.0
Installer >> ERS_JAVA2ONLY = Y
Installer >> ERS_JAVA2SUNONLY = N
Installer >> URL = https://w3.ibm.com/jct01008ws/tools/expenses/
Installer >> JAVA.VENDOR = SUN MICROSYSTEMS INC.
Installer >> Checking permissions - java vendor = SUN MICROSYSTEMS INC.
Installer >> OS.NAME = LINUX
Installer >> OS.ARCH = i386
Installer >> OS.VERSION = 2.6.35-28-generic-pae
Installer >> JAVA.VENDOR = SUN MICROSYSTEMS INC.
Installer >> JAVA.VERSION = 1.6.0_24
Installer >> OS = Other BROWSER = FireFox LAUNCH = Method 0 - Normal from local drive
Common Installer >> GXInstallerCommon version = 1,0,0,39
Common Installer >> SUN = true IE = false LINUX = true
Common Installer >> java version = 1.6.0_24 user.dir = /home/joshua home.dir = /home/joshua user.name = joshua
Installer >> ARCHIVE = exc.jar PACKED = false
Common Installer >> installDir = /home/joshua/.IBMERS
Common Installer >> ensureDir = /home/joshua/.IBMERS/IBMWW/
Installer >> INSTALLDIR = /home/joshua/.IBMERS/IBMWW
Installer >> otherVersion = null
Installer >> oldVersion = 4,6,0,42
Installer >> newVersion = 4,6,0,42
exception: Permission denied: file:/home/joshua/.IBMERS/IBMWW/.
java.lang.SecurityException: Permission denied: file:/home/joshua/.IBMERS/IBMWW/
	at sun.plugin2.applet.Plugin2Manager$AppletExecutionRunnable.run(Plugin2Manager.java:1483)
	at java.lang.Thread.run(Thread.java:662)
Exception: java.lang.SecurityException: Permission denied: file:/home/joshua/.IBMERS/IBMWW/
```

---

### Post by joshuapurcell on 2011-04-06
I've heard that this is related to the latest Java version, but I haven't installed an older version yet to see if that corrects the issue.

---

### Post by macflav on 2011-04-06
In my case, apparently it should work with the earlier version of the plugin, 1.6.0_14 (JRE 1.6.0_24 is fine, but the current version of the plugin has a compatibility issue with the applet I need to run).

Now I can't find a way to "downgrade" my plugin. Is there an easy way to do this? "Force Version" is unavailable on the Synaptic Package Manager...

---

### Post by macflav on 2011-10-25
After a fresh install of 11.10, firt I tried IcedTea. Applet wouldn't start (no error message). Then I installed Sun, and removed IcedTea. It worked! Not sure if it's the new Ubuntu or the install/remove that fixed the issue. I'm just happy it works.

---

