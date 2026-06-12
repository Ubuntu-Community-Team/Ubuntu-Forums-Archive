---
title: "Cant install anything! ACPID?"
date: 2009-07-17
forum: General Help
---

### Post by TheKLB on 2009-07-17
Everytime I try to install anything it keeps erroring out

```
admin@ks361414:~$ sudo apt-get install openssh-server                           Reading package lists... Done
Building dependency tree
Reading state information... Done
openssh-server is already the newest version.
openssh-server set to manually installed.
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.24-16-generic linux-headers-2.6.24-16
Use 'apt-get autoremove' to remove them.
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
admin@ks361414:~$ sudo /etc/init.d/acpid stop
 * Stopping ACPI services...                                             [ OK ]
admin@ks361414:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.24-16-generic linux-headers-2.6.24-16
Use 'apt-get autoremove' to remove them.
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
admin@ks361414:~$
admin@ks361414:~$ sudo /etc/init.d/acpid stop
 * Stopping ACPI services...                                             [ OK ]
admin@ks361414:~$ sudo killall hald
hald: no process killed


```

---

### Post by Tman5293 on 2009-07-17
You need to reinstall acpid cause its screwed up.

---

### Post by TheKLB on 2009-07-17
How do I go about doing that?

Ive tried removing it, rebooting, installing and still the same issue

---

