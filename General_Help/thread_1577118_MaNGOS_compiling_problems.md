---
title: "MaNGOS compiling problems"
date: 2010-09-18
forum: General Help
---

### Post by Kareta on 2010-09-18
After running
```

rpm --import http://dag.wieers.com/rpm/packages/RPM-GPG-KEY.dag.txt
```I got

```

error: http://dag.wieers.com/rpm/packages/RPM-GPG-KEY.dag.txt: import read failed(-1).
```also got another error message(are they related?):



```
$ rpm -Uvh rpmforge-release-0.3.6-1.el5.rf.x86_64.rpm
rpm: please use alien to install rpm packages on Debian, if you are really sure use --force-debian switch. See README.Debian for more details.


```Here's the guide I'm following: [http://getmangos.com/community/showthread.php?t=7839](http://getmangos.com/community/showthread.php?t=7839)

---

### Post by Kareta on 2010-09-18
Please help, sorry if it's something stupid or obvious but I really don't know what to do.

---

### Post by davidmohammed on 2010-09-18
you can't install an rpm file on a debian distro such as ubuntu.

You have to "alien" the rpm - have a read of this [thread]("http://ubuntuforums.org/showthread.php?t=1128807") on how to install and use alien to do this.

---

