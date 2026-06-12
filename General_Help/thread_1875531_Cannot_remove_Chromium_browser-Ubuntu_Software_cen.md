---
title: "Cannot remove Chromium browser-Ubuntu Software center"
date: 2011-11-04
forum: General Help
---

### Post by devarshi on 2011-11-04
Hello every one. i got some problem with chromium browser. i had installed the browser on my Pc . but during installation my pc got switched off because of no electricity . now. here is my problem . 

1] I am not able to remove Chromium browser from my pc. whenever i try to remove the browser from my pc using Ubuntu software center  i get following error on my screen-

installArchives() failed: dpkg: error processing chromium-browser (--remove): 
 Package is in a very bad inconsistent state - you should 
 reinstall it before attempting a removal. 
No apport report written because MaxReports is reached already 
Errors were encountered while processing: 
 chromium-browser

2] I tried to remove the browser from package manager  also . i got the same error. that the "package is too much inconsistent " . reinstall the browser it will help. 

3] i tried to remove the browser using purge command here is the error that i got on my terminal: 

devarshi@devarshi-desktop:~$ sudo apt-get --purge remove chromium-browser 
Reading package lists... Done 
Building dependency tree        
Reading state information... Done 
The following packages were automatically installed and are no longer required: 
  linux-headers-2.6.38-8 linux-headers-2.6.38-8-generic 
Use 'apt-get autoremove' to remove them. 
The following packages will be REMOVED: 
  chromium-browser* 
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded. 
1 not fully installed or removed. 
After this operation, 0 B of additional disk space will be used. 
Do you want to continue [Y/n]? y 
dpkg: error processing chromium-browser (--purge): 
 Package is in a very bad inconsistent state - you should 
 reinstall it before attempting a removal. 
Errors were encountered while processing: 
 chromium-browser 
E: Sub-process /usr/bin/dpkg returned an error code (1) 


4] i tried to download and install Google Chrome stable .deb file also . but the file does not install and the ubuntu OS hang itself. 


Someone please help . i am using Ubuntu 11.04:confused:

---

### Post by devarshi on 2011-11-04
And now. more to this i am not able to install the Eclipse software from ubuntu software center on my PC as well ... 

on software center i am getting the following error -
There seems to be a programming error in aptdaemon, the software that allows you to install/remove software and to perform other package management related tasks.

Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/aptdaemon/worker.py", line 961, in simulate
    trans.unauthenticated = self._simulate_helper(trans)
  File "/usr/lib/python2.7/dist-packages/aptdaemon/worker.py", line 1085, in _simulate_helper
    return depends, self._cache.required_download, \
  File "/usr/lib/python2.7/dist-packages/apt/cache.py", line 226, in required_download
    pm.get_archives(fetcher, self._list, self._records)
SystemError: E:I wasn't able to locate file for the chromium-browser package. This might mean you need to manually fix this package.

Now i am unable to install Eclipe environment on my pc . Some one plz help out.

---

### Post by cbowman57 on 2011-11-04
Open a terminal and attempt what it recommends, i.e. **sudo apt-get --reinstall install chromium**

See if that clears it up.

---

### Post by devarshi on 2011-11-04
I got this error msg. 

devarshi@devarshi-desktop:~$ sudo apt-get --reinstall install chromium
[sudo] password for devarshi: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package chromium is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  chromium-bsu

E: Package 'chromium' has no installation candidate

---

### Post by devarshi on 2011-11-04
Ohk thanks. anyways. 

I run the Update Manager . it installed some packages . n chromium browser by itself. and the things got back to normal. 

thanks for help .

---

