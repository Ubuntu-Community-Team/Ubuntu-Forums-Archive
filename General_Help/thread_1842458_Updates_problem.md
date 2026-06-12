---
title: "Updates problem"
date: 2011-09-11
forum: General Help
---

### Post by mcc28x on 2011-09-11
Hi 

I can't update my system I had a problem installing my printer, a Brother MFC465cn.

The software updater tells me there is a problem and to run "sudo apt-get install -f"

When I do this I get this output:

[I]Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED
  brmfcfaxlpd
0 upgraded, 0 newly installed, 1 to remove and 230 not upgraded.
1 not fully installed or removed.
After this operation, 115 kB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 156033 files and directories currently installed.)
Removing brmfcfaxlpd ...
start: Unknown job: lpd
dpkg: error processing brmfcfaxlpd (--remove):
 subprocess installed post-removal script returned error exit status 1
Errors were encountered while processing:
 brmfcfaxlpd
E: Sub-process /usr/bin/dpkg returned an error code (1)[/I]

How can I clear this problem up please?

Thanks

---

### Post by ubudog on 2011-09-11
Hi, try this:
[http://ubuntuforums.org/showpost.php?p=5445019&postcount=2](http://ubuntuforums.org/showpost.php?p=5445019&postcount=2)

Also, can you please post the output of:
```
uname -a
```

and:
```
sudo apt-get update
```

---

### Post by raja.genupula on 2011-09-11
```
sudo dpkg --configure -a
```

sudo apt-get update

do that in terminal and let us know what you got

---

### Post by mcc28x on 2011-09-11
Well I dived in and  edited the file /var/lib/dpkg/status file removing the references to the package in question. Solution from here:

[http://www.khattam.info/solved-subprocess-pre-removal-script-returned-error-exit-status-2-error-2009-08-04.html]("http://www.khattam.info/solved-subprocess-pre-removal-script-returned-error-exit-status-2-error-2009-08-04.html")

The Update Manager is working fine. The errant .deb was brmfcfaxlpd which I don't need or may try to reinstall at a later date.

I made backups just incase!

---

### Post by ubudog on 2011-09-11
Great!

---

