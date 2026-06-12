---
title: "SELinux Policy"
date: 2012-02-02
forum: General Help
---

### Post by abhi90 on 2012-02-02
what is Selinux policy.
and what function it does?
Does RAD installation requires SELinux policy disabled.
I am ubuntu 11.04

---

### Post by Dangertux on 2012-02-02
By default while Ubuntu's kernel is compiled with support for SELinux , SELinux is not installed.

Some installations would require SELinux be disabled due to policy conflicts (for instance in Fedora where SELinux is used).
if you choose to install on a distro that uses selinux you may wish to do the following prior to installing your RAID array.

```

sudo setenforce 0

```Prior to installing your device or edit /etc/selinux/config file and change the line

```

SELINUX=enforcing

```to 
```

SELINUX=permissive

```Hope this helps.

---

### Post by abhi90 on 2012-02-07
[SIZE=3]I am trying to install 'db2' but whenever I install db2 from terminal it shows me 'permission denied'  message. 
I think that requires SELinux to be disabled. I disable it by 'sudo setenforce 0' but still I got the same message.
while installing I login as a root user. 

what to do for it??
[/SIZE]

---

### Post by abhi90 on 2012-02-07
[SIZE=2]I am installing DB2 9.7 but when I type './db2setup -f sysreq'[/SIZE] it shows 
[SIZE=2]'bash: ./db2setup: Permission denied'[/SIZE].

[SIZE=2]what to do for it??

I see the file '[/SIZE]/etc/selinux/config' but the file doesn't have SELINUX=enforcing type in it.
It has  data:-
updateInfoAdded=true

[devicepreference.upd]
ctime=1317080216
done=DevicesMovedToPlatformPlugin,DevicesUIDsChanged
mtime=1298670852

[favicons.upd]
ctime=1317318276
done=kde3_2
mtime=1298670912

[kaccel.upd]
ctime=1317318279
done=kde3.3/r1
mtime=1298670888

[kcmdisplayrc.upd]
ctime=1317318279
done=kde3
mtime=1298670888

[kcookiescfg.upd]
ctime=1317080209
done=kde2.2/b1,kde3.1/cvs
mtime=1301666151

[kded.upd]
ctime=1317080209
done=kde3.0
mtime=1301666150

[kfmclient_3_2.upd]
ctime=1317318281
done=kfmclient_3_2
mtime=1298670912

[kio_help.upd]
ctime=1317080217
done=kde3_2
mtime=

---

