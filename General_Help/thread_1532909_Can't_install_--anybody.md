---
title: "Can't install --anybody?"
date: 2010-07-17
forum: General Help
---

### Post by inameiname on 2010-07-17
I just upgraded a few things just as usual, one being the newest Wine 1.2 that just came out, and for some reason, I continue to get this output, and am unable to resolve it. Anybody know how?

```
install wine
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information... Done
Initializing package states... Done       
The following partially installed packages will be configured:
  cups cups-driver-gutenprint ghostscript ghostscript-cups ghostscript-x 
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Setting up ghostscript (8.71.dfsg.2-0ubuntu1) ...
dpkg: error processing ghostscript (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of cups:
 cups depends on ghostscript; however:
  Package ghostscript is not configured yet.
dpkg: error processing cups (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ghostscript-cups:
 ghostscript-cups depends on ghostscript (>= 8.64.dfsg.1-0ubuntu10); however:
  Package ghostscript is not configured yet.
 ghostscript-cups depends on cups; however:
  Package cups is not configured yet.
dpkg: error processing ghostscript-cups (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of cups-driver-gutenprint:
 cups-driver-gutenprint depends on cups (>= 1.3.0); however:
  Package cups is not configured yet.
 cups-driver-gutenprint depends on ghostscript-cups; however:
  Package ghostscript-cups is not configureNo apport report written because the error message indicates its a followup error from a previous failure.
                                                                     No apport report written because the error message indicates its a followup error from a previous failure.
               No apport report written because MaxReports is reached already
                                                                             No apport report written because MaxReports is reached already
                                                           d yet.
dpkg: error processing cups-driver-gutenprint (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ghostscript-x:
 ghostscript-x depends on ghostscript (>= 8.63); however:
  Package ghostscript is not configured yet.
dpkg: error processing ghostscript-x (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 ghostscript
 cups
 ghostscript-cups
 cups-driver-gutenprint
 ghostscript-x
localepurge: Disk space freed in /usr/share/locale: 0 KiB
localepurge: Disk space freed in /usr/share/man: 0 KiB
localepurge: Disk space freed in /usr/share/gnome/help: 0 KiB
localepurge: Disk space freed in /usr/share/omf: 0 KiB
localepurge: Disk space freed in /usr/share/doc/kde/HTML: 0 KiB

Total disk space freed by localepurge: 0 KiB

E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up ghostscript (8.71.dfsg.2-0ubuntu1) ...
dpkg: error processing ghostscript (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of ghostscript-cups:
 ghostscript-cups depends on ghostscript (>= 8.64.dfsg.1-0ubuntu10); however:
  Package ghostscript is not configured yet.
dpkg: error processing ghostscript-cups (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of cups:
 cups depends on ghostscript; however:
  Package ghostscript is not configured yet.
dpkg: error processing cups (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of cups-driver-gutenprint:
 cups-driver-gutenprint depends on cups (>= 1.3.0); however:
  Package cups is not configured yet.
 cups-driver-gutenprint depends on ghostscript-cups; however:
  Package ghostscript-cups is not configured yet.
dpkg: error processing cups-driver-gutenprint (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ghostscript-x:
 ghostscript-x depends on ghostscript (>= 8.63); however:
  Package ghostscript is not configured yet.
dpkg: error processing ghostscript-x (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 ghostscript
 ghostscript-cups
 cups
 cups-driver-gutenprint
 ghostscript-x
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information... Done
Initializing package states... Done 

```

---

### Post by digitalcitizenx on 2010-07-17
Are you having an issue with how your system is running or with your printers?

---

### Post by inameiname on 2010-07-17
No, that's the thing. I don't nor have ever even had a printer hooked up to this computer. Thus, I'm unsure why cups and ghostscript (I'm guessing it has something to do with a printer), is all screwy all of a sudden. 

My system is running just fine other than having all of that pop up when trying to update anything using sudo apt-get update and sudo apt-get upgrade and etc. Not sure why this occurred, which only just happened based on the last bunch of updates that occurred, which included Wine, Rhythmbox, Radiotray, and a few others.

I'm just curious if there is anyway to finish installing the partially installed things that it keeps saying won't install.

Oh, and one thing I did install but remove fairly quickly which may or may not have had an effect is sudo apt-get install bluez-utils. Bluez was already installed of course, as it is included when first install Ubuntu Lucid, but I did install that yesterday, only to remove it an hour later after it seemed to do nothing and I was tired of playing with my bluetooth mobile. But that was just a sudo apt-get remove bluez and that's all.

---

### Post by inameiname on 2010-07-17
Alright, so out of curiosity I erased and restored my computer using a Remastersys custom DVD and then updated and I had no problems with the previously mentioned packages. Weird, but whatever.

---

### Post by digitalcitizenx on 2010-07-17
> **inameiname said:**
> Alright, so out of curiosity I erased and restored my computer using a Remastersys custom DVD and then updated and I had no problems with the previously mentioned packages. Weird, but whatever.

So....this is solved?

---

### Post by inameiname on 2010-07-18
Yeah. Well, solved as in I never figured out why, but seeing as how I restored my computer from an image and didn't have the issue, I say good enough.

---

### Post by cianca on 2010-07-18
I'm having the same issue here...

---

### Post by inameiname on 2010-07-19
Hmmm, that's weird, Cianca. Mine was nonexistent when I redid my whole computer, but it would've still been cool to have figured out how to resolve the issue. Maybe somebody will help on this posting.

---

