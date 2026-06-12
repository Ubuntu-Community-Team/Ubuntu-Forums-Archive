---
title: "Unable to share file"
date: 2012-03-20
forum: General Help
---

### Post by achu91 on 2012-03-20
I am having ubuntu11.10.When i tried to share a folder by right clicking of the desired folder and click sharing option , i stuck up with an error and unable to proceed further as i am very novice user of Ubuntu.

Pls help to solve this issue.

i have attached the screen shot for the error i have got.

Achuthan

---

### Post by raja.genupula on 2012-03-20
Hi open your terminal and type as 
```
sudo apt-get install -f
```

and let us know what you got .

---

### Post by achu91 on 2012-03-20
Thans for the reply i have done as per your instruction and below mentioned is the output

achuthan@achuthan-desktop:~$ sudo apt-get install -f
[sudo] password for achuthan: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up samba4 (4.0.0~alpha17~git20110807.dfsg1-1ubuntu1) ...
Administrator password will be set randomly!
Unknown parameter encountered: "max log size"
Ignoring unknown parameter "max log size"
Unknown parameter encountered: "syslog"
Ignoring unknown parameter "syslog"
Unknown parameter encountered: "passdb backend"
Ignoring unknown parameter "passdb backend"
Unknown parameter encountered: "unix password sync"
Ignoring unknown parameter "unix password sync"
Unknown parameter encountered: "passwd program"
Ignoring unknown parameter "passwd program"
Unknown parameter encountered: "pam password change"
Ignoring unknown parameter "pam password change"
Unknown parameter encountered: "map to guest"
Ignoring unknown parameter "map to guest"
Unknown parameter encountered: "usershare allow guests"
Ignoring unknown parameter "usershare allow guests"
Unknown parameter encountered: "guest ok"
Ignoring unknown parameter "guest ok"
Unknown parameter encountered: "guest ok"
Ignoring unknown parameter "guest ok"
Unknown parameter encountered: "max log size"
Ignoring unknown parameter "max log size"
Unknown parameter encountered: "syslog"
Ignoring unknown parameter "syslog"
Unknown parameter encountered: "passdb backend"
Ignoring unknown parameter "passdb backend"
Unknown parameter encountered: "unix password sync"
Ignoring unknown parameter "unix password sync"
Unknown parameter encountered: "passwd program"
Ignoring unknown parameter "passwd program"
Unknown parameter encountered: "pam password change"
Ignoring unknown parameter "pam password change"
Unknown parameter encountered: "map to guest"
Ignoring unknown parameter "map to guest"
Unknown parameter encountered: "usershare allow guests"
Ignoring unknown parameter "usershare allow guests"
Unknown parameter encountered: "guest ok"
Ignoring unknown parameter "guest ok"
Unknown parameter encountered: "guest ok"
Ignoring unknown parameter "guest ok"
Traceback (most recent call last):
  File "/usr/share/samba/setup/provision", line 256, in <module>
    useeadb=eadb, next_rid=opts.next_rid, lp=lp)
  File "/usr/lib/pymodules/python2.7/samba/provision/__init__.py", line 1602, in provision
    sitename=sitename)
  File "/usr/lib/pymodules/python2.7/samba/provision/__init__.py", line 584, in guess_names
    raise InvalidNetbiosName(netbiosname)
samba.provision.InvalidNetbiosName: The name ''ACHUTHAN-DESKTOP'' is not a valid NetBIOS name
dpkg: error processing samba4 (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 samba4
E: Sub-process /usr/bin/dpkg returned an error code (1)
achuthan@achuthan-desktop:~$

---

### Post by raja.genupula on 2012-03-20
what you got when you did this 
```
sudo dpkg-reconfigure samba4
```

---

### Post by Morbius1 on 2012-03-20
Sorry for the interruption but you definitely do not want to install Samba4:
> These packages contain snapshot versions of Samba 4, the next-generation version of Samba. These should be considered _experimental_, and should not be used in production.

---

### Post by achu91 on 2012-03-20
actually i want to access some shared printer and also access the windows network.So i googled and found that installing the samba will solve my problem hmmm .Is the any other way to do it?. pls let me know.

By the way the output for the command sudo dpkg-reconfigure samba4

is 

achuthan@achuthan-desktop:~$ sudo dpkg-reconfigure samba4
[sudo] password for achuthan: 
/usr/sbin/dpkg-reconfigure: samba4 is broken or not fully installed
achuthan@achuthan-desktop:~$ 
Also please suggest any alternative solution for my problem.

---

### Post by Morbius1 on 2012-03-20
** If you want to share a folder on your Ubuntu machine you will need to install Samba - not Samba4 which is in an alpha state of development but samba. If you have installed samba4 remove it and try to install samba instead.

** If you now want to access the shares or printers of some other machine on the lan then you need the samba client and that is installed by default.

As a side note your host name is too long for samba:
> achuthan-desktopThat can be fixed for networking purposes one you have a working smb.conf in place.

---

### Post by achu91 on 2012-03-20
that's wat i tried to initally ,i have attached an screen shot of what happened in my first post.Now having enede up here please guide me how to proceed further?. From you reply i could understand that samba client is installed as default.But when i open my printers thriugh the dash i am unable to find the list of shared printers.why is that so?.

---

### Post by Morbius1 on 2012-03-20
See if this will get you back to the something resembling the default state:

[1] Get rid of samba4:
```
sudo apt-get --purge remove samba4
sudo apt-get --purge remove samba4-common-bin
```[2] Install samba:
```
sudo apt-get install samba
sudo apt-get install samba-common
sudo apt-get install samba-common-bin
sudo apt-get install smbclient
sudo apt-get install python-smbc
```

---

### Post by achu91 on 2012-03-21
when i tried your first instruction ,i get an error.I have pasted the output below.This error i got when initially i tried to install samba.

achuthan@achuthan-desktop:~$ [COLOR="Red"]sudo apt-get install samba[/COLOR]
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

[COLOR="Blue"]The following packages have unmet dependencies:
 samba : Depends: samba-common (= 2:3.5.11~dfsg-1ubuntu2) but 2:3.5.11~dfsg-1ubuntu2.1 is to be installed
         Depends: libwbclient0 (= 2:3.5.11~dfsg-1ubuntu2) but 2:3.5.11~dfsg-1ubuntu2.1 is to be installed
E: Unable to correct problems, you have held broken packages.[/COLOR]

[COLOR="red"]Other commands also i have tried and output is pasetd below
achuthan@achuthan-desktop:~$ sudo apt-get install samba-common[/COLOR]
Reading package lists... Done
Building dependency tree       
Reading state information... Done
samba-common is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
[COLOR="red"]achuthan@achuthan-desktop:~$ sudo apt-get install samba-common-bin[/COLOR]
Reading package lists... Done
Building dependency tree       
Reading state information... Done
samba-common-bin is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
[COLOR="red"]achuthan@achuthan-desktop:~$ sudo apt-get install smbclient[/COLOR]
Reading package lists... Done
Building dependency tree       
Reading state information... Done
smbclient is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
[COLOR="Red"]achuthan@achuthan-desktop:~$ sudo apt-get install python-smbc[/COLOR]
Reading package lists... Done
Building dependency tree       
Reading state information... Done
python-smbc is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.


pls do reply

---

### Post by mastablasta on 2012-03-21
> **achu91 said:**
> But when i open my printers thriugh the dash i am unable to find the list of shared printers.why is that so?.
 
becuase you need to install (add) the printer first and then add their Samba windows folder as their location.
 
if you don't know where they are exactly the smbtree command should give you a clue to which folders you need to put in.

---

### Post by achu91 on 2012-03-21
Thanx okie i understood and did accordingly with out out much trouble.

But now how to install samba?. pls guide me

---

### Post by Morbius1 on 2012-03-21
Your packages seem to be all screwed up. My recommendation is to run the following commands:

```
sudo apt-get clean
``````
sudo apt-get update
```Then install the samba packages again.

If that doesn't do it change the title of your thread to: **Unable to install packages**. Samba or sharing in the title of the thread are avoided by most people but topics related to package management brings out the hard core linux folks.

---

### Post by HiImTye on 2012-03-21
```
sudo apt-get clean
sudo apt-get autoclean
sudo apt-get --purge autoremove
sudo apt-get update
```
then try to install samba again

---

### Post by achu91 on 2012-03-21
i tried all the ways told above but still getting the same error kindly help

[COLOR="Red"]achuthan@achuthan-desktop:~$ sudo apt-get install samba[/COLOR]
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 samba : Depends: samba-common (= 2:3.5.11~dfsg-1ubuntu2) but 2:3.5.11~dfsg-1ubuntu2.1 is to be installed
         Depends: libwbclient0 (= 2:3.5.11~dfsg-1ubuntu2) but 2:3.5.11~dfsg-1ubuntu2.1 is to be installed
E: Unable to correct problems, you have held broken packages.

---

### Post by Morbius1 on 2012-03-21
>   samba : Depends: samba-common (= 2:3.5.11~dfsg-1ubuntu2) but 2:3.5.11~dfsg-1ubuntu2.1 is to be installedThe samba package on a fully updated 11.10 install is in fact dependent on samba-common but not at the "2:3.5.11~dfsg-1ubuntu2" version. It should be dependent on the 2:3.5.11~dfsg-1ubuntu2.1 level. That means your packages are still discombobulated.

If you don't want to open this up to a wider audience then all I can offer is the following from [https://help.ubuntu.com/community/SynapticHowto:](https://help.ubuntu.com/community/SynapticHowto:)
> **Broken Upgrade or Installation**

 What to do if an installation process fails and you find it is no longer possible to install or remove packages: Open a Terminal and type the following commands, pressing the Return or Enter key after each (you may have to type in your [password]("https://help.ubuntu.com/community/RootSudo")): 
```
sudo dpkg --configure -a
``` ```
sudo apt-get install -f
```

---

### Post by achu91 on 2012-03-22
i have fond the solved this issue using below of mentioned thread.
[http://ubuntuforums.org/showthread.php?t=1944403](http://ubuntuforums.org/showthread.php?t=1944403)
Thanks all for all the suggestions and the help rendered.

---

