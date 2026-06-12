---
title: "clean up after a failed installation"
date: 2010-10-15
forum: General Help
---

### Post by watgrad on 2010-10-15
Hello - once again I come humbly before the awesome collective intelligence of *Ubuntu Forums*:

Made a mistake while installing btusp for macbook.  I know now that I shouldn't have deleted the installed files, I should have run "apt-get remove", but it's too late.  Now whenever I install software or updates I get an annoying message about the btusb packages:
[INDENT][COLOR="Navy"]Error! Cannot locate /usr/src/btusb-0.0.1.dkms.tar.gz.
File does not exist.
dpkg: error processing btusb-dkms (--configure):
subprocess installed post-installation script returned error exit status 2
No apport report written because MaxReports is reached already
Setting up oggconvert (0.3.3-1ubuntu1) ...
Errors were encountered while processing:
btusb-dkms
Setting up btusb-dkms (0.0.1) ...
Loading new btusb-0.0.1 DKMS files...

Error! Cannot locate /usr/src/btusb-0.0.1.dkms.tar.gz.
File does not exist.
dpkg: error processing btusb-dkms (--configure):
subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:[/COLOR][/INDENT]


I'd like to clean up apt/dpkg so that it doesn't think the package whose files I've deleted is still installed.  when I run

dpkg -l "btusb*"

I get this output:

[INDENT][COLOR="Navy"]Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
iF  btusb-dkms     0.0.1          Support for Apple MacbookPro v6 bluetooth.[/COLOR]
[/INDENT]

Any ideas how I go about removing this offending package...?

---

### Post by bobcollard on 2010-10-15
Try this:
```
sudo apt-get autoremove
```

---

### Post by watgrad on 2010-10-15
hi bob,

THanks for your help - sudo apt-get autoremove gave this error message:

[INDENT]Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up btusb-dkms (0.0.1) ...
Loading new btusb-0.0.1 DKMS files...

Error! Cannot locate /usr/src/btusb-0.0.1.dkms.tar.gz.
File does not exist.
dpkg: error processing btusb-dkms (--configure):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 btusb-dkms
E: Sub-process /usr/bin/dpkg returned an error code (1)
[/INDENT]

---

### Post by bobcollard on 2010-10-15
You could install it again and remove it correctly.

---

