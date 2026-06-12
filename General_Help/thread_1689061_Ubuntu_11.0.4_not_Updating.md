---
title: "Ubuntu 11.0.4 not Updating"
date: 2011-02-16
forum: General Help
---

### Post by meanpt on 2011-02-16
From ths morning's 41 updates only one installed. Errors listed below. Any Help? Regards.

installArchives() failed:  Extracting templates from packages: 75%% Extracting templates from packages: 100%% 
Preconfiguring packages ... 
 Extracting templates from packages: 75%% Extracting templates from packages: 100%% 
Preconfiguring packages ... 
(Reading database ...  (Reading database ... 5%% (Reading database ... 10%% (Reading database ... 15%% (Reading database ... 20%% (Reading database ... 25%% (Reading database ... 30%% (Reading database ... 35%% (Reading database ... 40%% (Reading database ... 45%% (Reading database ... 50%% (Reading database ... 55%% (Reading database ... 60%% (Reading database ... 65%% (Reading database ... 70%% (Reading database ... 75%% (Reading database ... 80%% (Reading database ... 85%% (Reading database ... 90%% (Reading database ... 95%% (Reading database ... 100%% (Reading database ... 174724 files and directories currently installed.) 
Preparing to replace mount 2.17.2-3.3ubuntu4 (using .../mount_2.17.2-9.1ubuntu1_i386.deb) ... 
/var/lib/dpkg/tmp.ci/preinst: 49: dpkg-vendor: not found 
dpkg: error processing /var/cache/apt/archives/mount_2.17.2-9.1ubuntu1_i386.deb (--unpack): 
 subprocess new pre-installation script returned error exit status 127 
No apport report written because MaxReports is reached already
Errors were encountered while processing: 
 /var/cache/apt/archives/mount_2.17.2-9.1ubuntu1_i386.deb

---

### Post by clhsharky on 2011-02-16
meanpt


Ubuntu 11.04 has not been released yet,and belongs in

Development & Programming>Natty Narwhal Testing and Discussion
[http://ubuntuforums.org/forumdisplay.php?f=394](http://ubuntuforums.org/forumdisplay.php?f=394)

Sticky's very helpful,"Partial Upgrade".


Sharky

---

### Post by meanpt on 2011-02-16
Hi Sharky

Thanks for the hint. I went there but the problem reported as a partial update do not seemed to be similar to the one I experienced. In the meanwhile, during my local afternoon new updates were made available and a cumulated total of 54 updates were installed without this error, meaning some update may have solved it.

Again, many thanks.

---

### Post by David D. on 2011-02-16
A number of people have had trouble updating due to a bug (myself included).  The bug report [https://bugs.launchpad.net/bugs/719754](https://bugs.launchpad.net/bugs/719754) has a workaround which worked for me.  The workaround is to install dpkg-dev, then run your updates.  The updates added later in the day corrected the bug, so that is why you were able to update with the additional number of update files.

---

### Post by meanpt on 2011-02-17
:) ... thanks, David :)

---

