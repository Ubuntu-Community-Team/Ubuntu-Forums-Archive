---
title: "ISCSI Target Help"
date: 2011-12-02
forum: General Help
---

### Post by Ncage1974 on 2011-12-02
Guys definitely not a pro at linux by a long shot. This is probably the first of many questions i will ask :)

I'm coming to linux from freeNAS because of frustration with the direction then went (6GB+ RAM Recommendation)

I'm following the following tutorial:
[http://www.howtoforge.com/using-iscsi-on-ubuntu-10.04-initiator-and-target](http://www.howtoforge.com/using-iscsi-on-ubuntu-10.04-initiator-and-target)

Its the most recent tutorial i could find on setting up an iscsi target. Is there a better one out there? Especially one that offers alot of explanation (hate doing something when i don't understand it).

First question i had was on the ietd.conf file. I want to use the entire /dev/sdb hard drive so i guessed that the configuration file should read:
Lun 0 Path=/dev/sdb/storage_lun1,Type=fileio
but of course i'm not sure.

Second, there wasn't a /etc/initiators.allow file. I created a new one but i would think it should have existed if the tutorial was correct

Third, when i try to start the service:
/etc/init.d/iscsitarget start
i get the following error:
FATAL: Module iscsi_trgt not found.    [fail]

I'm using ubuntu server 11.04.

Any help would be greatly appreciated.

thanks,
Ncage

---

### Post by Ncage1974 on 2011-12-02
OK got it partially figured out (at least the error message):
[http://sys-admin.wikidot.com/install-iscsi-target](http://sys-admin.wikidot.com/install-iscsi-target)

but when i go through the steps to fix it
m-a a-i iscsitarget 

i get the following generic error:
Build of the package iscsitarget failed! How do you wish to proceed?

When i examine the log file all i see is:
Build log starting, file:
/var/cache/modass/iscsitarget.buildlog.3.0.0-12-generic.1322885366
Date: Fri, 02 Dec 2011

---

### Post by thaelim on 2011-12-02
Those are very old instructions... 

I use an Ubuntu iSCSI system every day at work, so I might be able to help ;)

First suggestion is to use tgt instead of iscsi-target. tgt is very easy to configure and works very well.

Second suggestion would be to install Ubuntu Server 11.10. There are bugs in older versions of tgt that cause data corruption which I'm guessing your probably want to avoid.

tgt's configuration file resides at /etc/tgt/targets.conf, and contains a bunch of useful examples on how to configure it.

---

### Post by Ncage1974 on 2011-12-03
> **thaelim said:**
> Those are very old instructions... 

I use an Ubuntu iSCSI system every day at work, so I might be able to help ;)

First suggestion is to use tgt instead of iscsi-target. tgt is very easy to configure and works very well.

Second suggestion would be to install Ubuntu Server 11.10. There are bugs in older versions of tgt that cause data corruption which I'm guessing your probably want to avoid.

tgt's configuration file resides at /etc/tgt/targets.conf, and contains a bunch of useful examples on how to configure it.

Thanks for the reply. Thats the problem with the internet....what your reading can be outdated in a lot of cases. I will try to use tgt and let you know what happens :).

---

### Post by Ncage1974 on 2011-12-03
> **thaelim said:**
> Those are very old instructions... 

I use an Ubuntu iSCSI system every day at work, so I might be able to help ;)

First suggestion is to use tgt instead of iscsi-target. tgt is very easy to configure and works very well.

Second suggestion would be to install Ubuntu Server 11.10. There are bugs in older versions of tgt that cause data corruption which I'm guessing your probably want to avoid.

tgt's configuration file resides at /etc/tgt/targets.conf, and contains a bunch of useful examples on how to configure it.

Ok i think i'm close my targets.conf:
<target iqn.2008-09.com.example:server.target4>
   direct-store /dev/sdb
</target>

When i do a sudo tgtadm --lld iscsi --op show --mode target i get
LUN: 0
 Type Controller
 .....

LUN: 1
  Type Disk
  .....
  Online: Yes
  

When i try to connect from Windows 7 i can see it in the discovery tab by both:
iqn.2008-09.com.example:server.target4
and ip address: 
192.168.5.5

but when i try to do a quick connect with either the ip address or "iqn.2008-09.com.example:server.target4" i get:
No Targets available for Login using Quick Connect

---

### Post by thaelim on 2011-12-04
You might be better off asking that one in a Windows forum. You can check though whether the iSCSI target is listening:

```
netstat -an | grep LISTEN
```

You should see an entry for TCP 0.0.0.0:3260

---

### Post by Ncage1974 on 2011-12-04
> **thaelim said:**
> You might be better off asking that one in a Windows forum. You can check though whether the iSCSI target is listening:

```
netstat -an | grep LISTEN
```

You should see an entry for TCP 0.0.0.0:3260


Thanks for all the help. I finally got it working but i don't know why what i did fixed it. Windows 7 iSCSI initiator is pretty easy. if you type in the ip address of the iscsi target it should work. 

Anyways according to the docs on the targets.conf (targets.conf.example):
# Sample target with one LUN only. Defaults to allow access for all initiators:

<target iqn.2008-09.com.example:server.target1>
    backing-store /dev/LVM/somedevice
</target>


You will see above that it defaults to all access but when i did a tgtadm --lld iscsi --op show --mode target

LUN: 1
   ....
  ACL information:

As you can see the ACL information is blank which is key. 

To fix it i did: 
tgtadm --lld iscsi --op bind --mode target --tid 1 -I ALL

which resulted in

LUN: 1
  ACL information:
  ALL

don't understand why i had to do this when it specifically states it defaults to all and i don't want to run this command every time i reboot.

---

### Post by thaelim on 2011-12-05
I would say that's a bug - the latest version of tgt (in Fedora 16) definitely doesn't have this problem. You might be able to get around it by specifying access control details in targets.conf

---

### Post by Ncage1974 on 2011-12-06
> **thaelim said:**
> I would say that's a bug - the latest version of tgt (in Fedora 16) definitely doesn't have this problem. You might be able to get around it by specifying access control details in targets.conf

Again thanks for all your help. I just want to make this thread complete for anyone having the same issue. Unfortunately in the targets.conf example there nothing to tell you how to provide the "ALL" option since it is suppose to be the default. Anyways this is how you do it:

<target iqn.2005-08.com.example:myserver.target6>
          direct-store /dev/sdb ALL
</target>

Hopefully this saves someone hours of headaches :)

---

