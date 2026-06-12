---
title: "package held back on update but why?"
date: 2012-02-03
forum: General Help
---

### Post by ianc1 on 2012-02-03
For a while now on running```
sudo apt-get update && sudo apt-get upgrade
```I have been getting the following```
The following packages have been kept back:
  boot-repair-common
```Can anyone explain why as I am very puzzled?

Thanks in advance.

---

### Post by plucky on 2012-02-03
> The following packages have been kept back:
  boot-repair-common


What does ```
sudo apt-get dist-upgrade
``` show you?

It usually means there is a dependency problem that dist-upgrade will show you and hopefully fix.

Good Luck

---

### Post by ianc1 on 2012-02-08
Hi Plucky

Many thanks for the fast response and apologies for the slow reply.  I have tried the dist-upgrade option and this pulled in and installed one extra package boot-repair but still left me with the package boot-repair-common kept back.

After a further sudo apt-get update && sudo apt-get upgrade this is still the case.

Any ideas?

Thanks

---

### Post by drmrgd on 2012-02-08
I think if you run:

```
sudo apt-get install boot-repair-common
```

You may be able to induce an error message to say why it's being held back.  It's probably a dependency issue, but hard to say what that dependency is and why dist-upgrade is not satisfying it.

---

### Post by ianc1 on 2012-02-08
Thanks.  Hadn't considered that.  Just ran the command and get the following result:```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  boot-sav-gui cups-pk-helper
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  clean-ubiquity-common
The following packages will be upgraded:
  boot-repair-common
1 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 231 kB of archives.
After this operation, 942 kB of additional disk space will be used.
Do you want to continue [Y/n]?
```How do I know whether I'm better off with what's installed already ie clean-ubiquity-common or with the held-back package boot-repair-common?

---

### Post by stoneage on 2012-02-08
You stopped too soon. Press y then Enter, then post the error message, if any.

---

### Post by ianc1 on 2012-02-08
Ah, I thought the error would have come at this point.  So the error was```
Get:1 http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/ oneiric/main boot-repair-common all 3.04-0ppa3~oneiric [231 kB]
Fetched 231 kB in 0s (466 kB/s)            
(Reading database ... 250566 files and directories currently installed.)
Removing clean-ubiquity-common ...
Processing triggers for python-support ...
(Reading database ... 250563 files and directories currently installed.)
Preparing to replace boot-repair-common 3.01-0ppa12~oneiric (using .../boot-repair-common_3.04-0ppa3~oneiric_all.deb) ...
Unpacking replacement boot-repair-common ...
dpkg: error processing /var/cache/apt/archives/boot-repair-common_3.04-0ppa3~oneiric_all.deb (--unpack):
 trying to overwrite '/usr/share/clean/clean-gui-tab-loca.sh', which is also in package clean-gui 3.04-0ppa3~oneiric
No apport report written because MaxReports is reached already
                                                              dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Processing triggers for python-support ...
Errors were encountered while processing:
 /var/cache/apt/archives/boot-repair-common_3.04-0ppa3~oneiric_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```I guess the problem is therefore of my own doing ie the PPA thats installed.  I can't remember why or when I installed it though.

---

### Post by stoneage on 2012-02-08
Are you still running Natty ? It looks like you have some Oneiric ppa s enabled.

---

### Post by ianc1 on 2012-02-09
Sorry Stoneage, that was misleading.  I failed to update my profile; I am now and have been since it came out running 11.10.  Hopefully my profile now indicates this.

---

