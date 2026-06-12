---
title: "apt trouble!!"
date: 2009-09-20
forum: General Help
---

### Post by rudi009 on 2009-09-20
i tried to install jdk a few days back using apt  and failed and now whenever i try to install any new program things related to jdk start appearing..following appeared when i tried to install nmap:
//////////////////////
sharma@sharma-laptop:~$ sudo apt-get install nmap
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.28-11 java-common unixodbc linux-headers-2.6.28-11-generic
  odbcinst1debian1
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  nmap
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
Need to get 1187kB of archives.
After this operation, 4502kB of additional disk space will be used.
Get:1 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty/main nmap 4.76-0ubuntu4 [1187kB]
Fetched 1187kB in 2s (413kB/s)
Selecting previously deselected package nmap.
(Reading database ... 146451 files and directories currently installed.)
Unpacking nmap (from .../nmap_4.76-0ubuntu4_i386.deb) ...
Processing triggers for man-db ...
Setting up sun-java5-doc (1.5.0-19-0ubuntu0.9.04) ...
This package is an installer package, it does not actually contain the
J2SDK documentation.  You will need to go download one of the
archives:

    jdk-1_5_0-doc.zip jdk-1_5_0-doc-ja.zip

(choose the non-update version if this is the first installation).
Please visit

    [http://java.sun.com/j2se/1.5.0/download.html](http://java.sun.com/j2se/1.5.0/download.html)

now and download.  The file should be owned by root.root and be copied
to /tmp.

[Press RETURN to try again, 'no' + RETURN to abort] 
///////////////
please help.:confused:

---

### Post by KiLaHuRtZ on 2009-09-20
Try updating your sources...

```
sudo apt-get update
```

If that does not work, try purging JDK...

```
sudo apt-get purge jdk
```

---

### Post by rudi009 on 2009-09-21
no success..................:(

---

### Post by stumbleUpon on 2009-09-21
> **rudi009 said:**
> i tried to install jdk a few days back using apt  and failed and now whenever i try to install any new program things related to jdk start appearing..following appeared when i tried to install nmap:
//////////////////////
sharma@sharma-laptop:~$ sudo apt-get install nmap
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.28-11 java-common unixodbc linux-headers-2.6.28-11-generic
  odbcinst1debian1
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  nmap
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
Need to get 1187kB of archives.
After this operation, 4502kB of additional disk space will be used.
Get:1 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty/main nmap 4.76-0ubuntu4 [1187kB]
Fetched 1187kB in 2s (413kB/s)
Selecting previously deselected package nmap.
(Reading database ... 146451 files and directories currently installed.)
Unpacking nmap (from .../nmap_4.76-0ubuntu4_i386.deb) ...
Processing triggers for man-db ...
Setting up sun-java5-doc (1.5.0-19-0ubuntu0.9.04) ...
This package is an installer package, it does not actually contain the
J2SDK documentation.  You will need to go download one of the
archives:

    jdk-1_5_0-doc.zip jdk-1_5_0-doc-ja.zip

(choose the non-update version if this is the first installation).
Please visit

    [http://java.sun.com/j2se/1.5.0/download.html](http://java.sun.com/j2se/1.5.0/download.html)

now and download.  The file should be owned by root.root and be copied
to /tmp.

[Press RETURN to try again, 'no' + RETURN to abort] 
///////////////
please help.:confused:


Go to the sun site mentioned 
[http://java.sun.com/j2se/1.5.0/download.html](http://java.sun.com/j2se/1.5.0/download.html)

and download the file jdk-1_5_0-doc.zip which is about 44 MB in size. Save the file in the /tmp folder. Navigate to this folder in a terminal and enter the following command

```
sudo chown root:root jdk-1_5_0-doc.zip 
```

Then run apt-get again (sudo apt-get update). This will look for the file in the /tmp folder and install it. After that you will be informed that you can delete the jdk-1_5_0-doc.zip file if you want.

---

