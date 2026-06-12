---
title: "Using WPA on Ubuntu 5.10"
date: 2006-01-29
forum: General Help
---

### Post by kent41 on 2006-01-29
hi

I am using Ubuntu Ver. 5.10  and need to connect to a router using WPA security and I only see WEP on the Config screen. Is it possible to use WPA on ver. 5.10 or do I need to download other code.
 Thanks 
 Kent41

---

### Post by Gcool on 2006-01-29
It is perfectly possible to use wpa under ubuntu. You'll need a package called wpa supplicant for this.

[This]("https://wiki.ubuntu.com/WPAHowto") page should give you all the info you need.

---

### Post by hw-tph on 2006-01-30
You may want to read [this](http://prinsig.se/weekee/index.php/Ubuntu#Broadcom_WLAN) that I wrote regarding using WPA and ndiswrapper on the Compaq R3000 series laptops. 


Håkan

---

### Post by kent41 on 2006-02-09
i have a new problem.i am trying to install CLAMAV with the following code.
  
  "sudo apt-get install clamav"
Reading package lists... Done
Building dependency tree... Done
Package clamav is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package clamav has no installation candidate

 OR i tried this one 

kent@GPS-2:~$ sudo apt-get install clamav-0.88.tar.gz
The error message i receive is 

Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package clamav-0.88.tar.gz

Any one with ideas on how to install  clamav anti-virus

---

### Post by hw-tph on 2006-02-10
clamav is in the Universe repository. Read the [Adding respositories howto](https://wiki.ubuntu.com/AddingRepositoriesHowto) and when Universe is added you should have no problem apt-getting clamav.


Håkan

---

### Post by kent41 on 2006-02-10
[QUOTE=hw-tph]clamav is in the Universe repository. Read the [Adding respositories howto](https://wiki.ubuntu.com/AddingRepositoriesHowto) and when Universe is added you should have no problem apt-getting clamav.


Håkan[/QUOTE]
this is what i got at the end of the build- what does it mean ?

 Package clamav-base is not configured yet.
dpkg: error processing clamav-freshclam (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of clamav:
 clamav depends on clamav-freshclam | clamav-data; however:
  Package clamav-freshclam is not configured yet.
  Package clamav-data is not installed.
  Package clamav-freshclam which provides clamav-data is not configured yet.
dpkg: error processing clamav (--configure):
 dependency problems - leaving unconfigured
Setting up libgmpxx3 (4.1.4-10ubuntu1) ...

Setting up libgmp3c2 (4.1.4-10ubuntu1) ...

Setting up libclamav1 (0.87-1) ...

Errors were encountered while processing:
 clamav-base
 clamav-freshclam
 clamav
E: Sub-process /usr/bin/dpkg returned an error code (1)
kent@GPS-2:~$

---

### Post by kent41 on 2006-02-10
ok i got clamav to run with the command line input. However i got the messages
"You are running an old version of Clamav" ok i then downloaded the .88 version
and when i try to install the .88 version i get the message you are already using
the most up to data version of clamav  .87.

also at the end of the running of clamav the details say that clamav has found 9 virus.
ok how do i delete these virus file or does Clamav only tell me i have a virus?

and is the command line the only way to run Clamav? if it is i am out of here and
back to XP at least i can get rid of virus and it not quit as stressful.

Thanks for you help so far Kent41

---

