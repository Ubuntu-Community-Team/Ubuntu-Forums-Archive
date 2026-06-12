---
title: "Cannot install any aplication."
date: 2009-10-06
forum: General Help
---

### Post by n0an on 2009-10-06
Hello,

I did a reboot after installing FileZilla and Unrar, and I am getting this error when installing any new application. Hey, I also installed updates and I think this is happening since then.


```
admin@server96:~$ sudo apt-get install proftpd gproftpd
Reading package lists... Done
Building dependency tree       
Reading state information... Done
proftpd is already the newest version.
gproftpd is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up acpid (1.0.4-5ubuntu9.3) ...
* Starting ACPI services... acpid: can't open /proc/acpi/event: No such file or directory
invoke-rc.d: initscript acpid, action "start" failed.
dpkg: error processing acpid (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 acpid
E: Sub-process /usr/bin/dpkg returned an error code (1)
```Could you please tell me how to fix it? I get the same error on command line and Synaptics Manager. Please be a little detailed as I am not a pro with Linux. 

Thanks!

---

### Post by minigeek on 2009-10-06
> **n0an said:**
> Hello,

I did a reboot after installing FileZilla and Unrar, and I am getting this error when installing any new application. Hey, I also installed updates and I think this is happening since then.


```
admin@server96:~$ sudo apt-get install proftpd gproftpd
Reading package lists... Done
Building dependency tree       
Reading state information... Done
proftpd is already the newest version.
gproftpd is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up acpid (1.0.4-5ubuntu9.3) ...
* Starting ACPI services... acpid: can't open /proc/acpi/event: No such file or directory
invoke-rc.d: initscript acpid, action "start" failed.
dpkg: error processing acpid (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 acpid
E: Sub-process /usr/bin/dpkg returned an error code (1)
```Could you please tell me how to fix it? I get the same error on command line and Synaptics Manager. Please be a little detailed as I am not a pro with Linux. 

Thanks!

Hi

The following package seems to have failed to be install
[B]
1 not fully installed or removed.[/B]

Run the following command in a terminal

sudo apt-get autoclean

:)

---

### Post by n0an on 2009-10-06
Still same...

```
admin@server96:~$ sudo apt-get install proftpd gproftpd
Reading package lists... Done
Building dependency tree       
Reading state information... Done
proftpd is already the newest version.
gproftpd is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up acpid (1.0.4-5ubuntu9.3) ...
 * Starting ACPI services...                                                    acpid: can't open /proc/acpi/event: No such file or directory
invoke-rc.d: initscript acpid, action "start" failed.
dpkg: error processing acpid (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 acpid
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by n0an on 2009-10-06
I did an update of ACPID and that seems to be the problem Any idea how to downgrade? Here's the link to the packages:

[https://launchpad.net/ubuntu/+source/acpid](https://launchpad.net/ubuntu/+source/acpid)

Thanks!

---

### Post by minigeek on 2009-10-06
> **n0an said:**
> Still same...

```
admin@server96:~$ sudo apt-get install proftpd gproftpd
Reading package lists... Done
Building dependency tree       
Reading state information... Done
proftpd is already the newest version.
gproftpd is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up acpid (1.0.4-5ubuntu9.3) ...
 * Starting ACPI services...                                                    acpid: can't open /proc/acpi/event: No such file or directory
invoke-rc.d: initscript acpid, action "start" failed.
dpkg: error processing acpid (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 acpid
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

[http://ubuntuforums.org/showthread.php?t=394282](http://ubuntuforums.org/showthread.php?t=394282)

sudo apt-get --purge remove <package>

---

### Post by n0an on 2009-10-06
I did that. proftpd installed, but I am unable to connect. I get this in the ftp client:

> SSH-2.0-OpenSSH_4.7p1 Debian-8ubuntu1.2

---

