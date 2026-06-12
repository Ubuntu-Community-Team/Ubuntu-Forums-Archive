---
title: "In Karmic NFS secondary group permissions do not work"
date: 2010-01-04
forum: General Help
---

### Post by jmb365 on 2010-01-04
I have a very unique problem that I have not found an answer to nor have been able to solve after much searching (Googling)

I have a Fedora 7 PC acting as the NFS server.  I have two users as follows on other Ubuntu (various flavors) based client PCs:

```

id ks
uid=1000(ks) gid=1000(ks) groups=1000(ks),4(adm),20(dialout),21(fax),24(cdrom),26(tape),29(audio),30(dip),44(video),46(plugdev),103(fuse),104(lpadmin),112(netdev),115(admin),120(sambashare),1999(family),1100(parents),123(mythtv)

id js
uid=1001(js) gid=1001(js) groups=1001(js),4(adm),20(dialout),21(fax),24(cdrom),26(tape),29(audio),30(dip),44(video),46(plugdev),103(fuse),104(lpadmin),112(netdev),115(admin),120(sambashare),1999(family),1100(parents)

```

Note that both of them also belong to the groups "family" and "parents".

When "ks" tries the following he gets:

```

ls -al /home/family
total 516
drwxrwx--- 20 ks   family  4096 2010-01-04 13:42 .
drwxr-xr-x 13 root root    4096 2009-12-27 20:55 ..
drwxrwx---  3 ks   family  4096 2009-07-24 09:07 Health
etc...

```

When "js" tries the following in an Ubuntu Karmic PC he gets:

```

ls -al /home/family
ls: cannot open directory /home/family: Permission denied

```

Even though "family" members have "rwx" permissions to /home/family, it does not work.  But the same works just fine on any other version of Ubuntu.  It appears the secondary group permissions in Ubuntu Karmic are broken or changed.  I have tried the suggestion "Remove --manage-gids in /etc/default/nfs-kernel-server" posted at [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/409366](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/409366), but have seen no replies yet.  Any suggestions or advice is appreciated!

Thanks
JMB

---

### Post by bodhi.zazen on 2010-01-04
Are those permissions on the client or the server ?

---

### Post by jmb365 on 2010-01-04
> **bodhi.zazen said:**
> Are those permissions on the client or the server ?

Thank you for replying.  All the code segments of my first email are from the Karmic client PC.  Also I have taken care to match the UIDs and GIDs on the server and all the clients.  I am using the same entry in the /etc/fstab file of the Karmic (and older) Ubuntu client PCs as shown below:

```

linux0:/home/family	/home/family	nfs	auto,exec,bg	0 0

```
"linux0" is the NFS server running Fedora7; which has the following in /etc/exports:
```

/home/family 192.168.1.0/24(rw,secure,sync,no_wdelay,no_root_squash)

```

Hope I have answered your question.

Regards,
JMB

---

### Post by bodhi.zazen on 2010-01-05
According to this link :

[https://help.ubuntu.com/community/SettingUpNFSHowTo#Group%20Permissions](https://help.ubuntu.com/community/SettingUpNFSHowTo#Group%20Permissions)

**emphasis added by myself**.

> With NFS, a user's access to files is determined by his/her membership of groups on the client, not on the server. **However, there is an important limitation: a maximum of 16 groups are passed from the client to the server, and, if a user is member of more than 16 groups on the client, some files or directories might be unexpectedly inaccessible.**With this advice in mind, can we reduce the number of groups your users are in ?

---

### Post by jmb365 on 2010-01-05
> **bodhi.zazen said:**
> According to this link :

[https://help.ubuntu.com/community/SettingUpNFSHowTo#Group%20Permissions](https://help.ubuntu.com/community/SettingUpNFSHowTo#Group%20Permissions)

**emphasis added by myself**.

With this advice in mind, can we reduce the number of groups your users are in ?

Thank you very much for that tip.  It solved my problem. :)  Thank you also for the detailed references you provided which have enriched my understanding of NFS and more!  I have corrected my posting in bugs.launchpad as well.  Ubuntu is not only a great Linux flavour but provides excellent and timely technical help from wonderful people like you.  Thank you!

Regards
JMB

---

