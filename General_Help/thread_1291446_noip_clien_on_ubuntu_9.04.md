---
title: "noip clien on ubuntu 9.04"
date: 2009-10-14
forum: General Help
---

### Post by luisfra on 2009-10-14
ok fist this is my first time using ubuntu has mi primary os, so yes i'm a noob!! the thing is that i'm trying to install noip client and  everything whent well untill the last part here is a copy of the log!!

luisfra@luisfra-desktop:~$ sudo apt-get install no-ip
[sudo] password for luisfra: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting noip2 instead of no-ip
The following NEW packages will be installed:
  noip2
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/82.2kB of archives.
After this operation, 242kB of additional disk space will be used.
Preconfiguring packages ...
Selecting previously deselected package noip2.
(Reading database ... 108066 files and directories currently installed.)
Unpacking noip2 (from .../noip2_2.1.9-1_i386.deb) ...
Processing triggers for man-db ...
Setting up noip2 (2.1.9-1) ...

Configuration file '/usr/local/etc/no-ip2.conf' is in use by process 2284.
Ending!

dpkg: error processing noip2 (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 noip2
E: Sub-process /usr/bin/dpkg returned an error code (1)

everytime i try to create a config file i get this!!

uisfra@luisfra-desktop:~$ noip2 -C

Auto configuration for Linux client of no-ip.com.

Can't create config file (/usr/local/etc/no-ip2.conf)
Permission denied
Re-run noip, adding '-c configfilename' as a parameter.

any help will be great!! this the only prob i have been having everything else is working great

---

### Post by P4man on 2009-10-14
add sudo in front if you want to make that file in /usr/local/etc/

```
sudo noip2 -C
```

Sudo elevates you to root permission, your user has no rights to write to /usr without it.

Alternatively, put the configuration file in your home folder with

```
noip2 -C -c ~/mynoipconfigfile
```

After that, you'll need to start noip2 referencing the correct config file. Eg 
```
noip2 -c ~/mynoipconfigfile
```

---

### Post by luisfra on 2009-10-14
thanks it works like a charm!! now i just hope it refresh!!

One last question i put the script so noip will start when the system boots, how do i know that it starts cause i don't see it on System Monitor!! or that ok!! thanks for the quick reply

Edit: i'm still geting this error!!

Configuration file '/usr/local/etc/no-ip2.conf' is in use by process 2293.
Ending!

dpkg: error processing noip2 (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 noip2
E: Sub-process /usr/bin/dpkg returned an error code (1)

don't know why but that was when installing some ati drivers!!

Edit2: ok nevermind i found out that my modem had the dynamic DNS option!! thanks anyways

---

### Post by P4man on 2009-10-15
> **luisfra said:**
> thanks it works like a charm!! now i just hope it refresh!!

One last question i put the script so noip will start when the system boots, how do i know that it starts cause i don't see it on System Monitor!! or that ok!! thanks for the quick reply

Edit: i'm still geting this error!!

Configuration file '/usr/local/etc/no-ip2.conf' is in use by process 2293.
Ending!

dpkg: error processing noip2 (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 noip2
E: Sub-process /usr/bin/dpkg returned an error code (1)

don't know why but that was when installing some ati drivers!!

Edit2: ok nevermind i found out that my modem had the dynamic DNS option!! thanks anyways

Well, even if its no longer necessary, it looks like noip2 is already running, hence the configuration file is in use. You're trying to start it a second time. If you don't see it in system monitor, its probably because you're only looking at your own processes. Go to View and select "show ALL processes", and Im pretty sure it will show up there. And yes it does update.

---

### Post by luisfra on 2009-10-15
thank you for everything!! and yes i see it now in the system monitor!!

---

