---
title: "NFS share through IPv6"
date: 2011-05-07
forum: General Help
---

### Post by jæs on 2011-05-07
Hi everyone,

Earlier I tried to reconfigure my existing (and working) NFS shares with some local scope IPv6 addresses.

Here comes the line I wrote on the /etc/exports of my server (Debian, running NFSv4. I read this version is compatible with IPv6 plus, when I launch the nfs-kernel-server daemon, no error is printed, so the issue shouldn't be here).
```
/srv/partage    [fe80::225:22ff:fe06:b11c%eth0](rw,async,subtree_check,anonuid=1000,anongid=1000,all_squash)
```Here is the line I added to my /etc/fstab. The preexisting IPv4 conf was working with the same line except it had IPv4 instead of course.
```
[fe80::221:91ff:fe96:d6a8%eth0]:/srv/partage           /media/Midgard  nfs     defaults,noauto,users 0 0
```And here comes the bug, when I try to mount the distant share on my Ubuntu Natty, I get this : 
```
jaes@Nibelheim:~$ mount /media/Midgard 
mount.nfs: Failed to resolve server fe80::221:91ff:fe96:d6a8%eth0: Address family for hostname not supported
```I tried to install a 1.2.3 version of nfs-common which was packaged for an older ubuntu but it didn't change anything from my (many) tries with 1.2.2.

So that's kinda all I got for now. Atfer many searches I couldn't determine if IPv6 is totally incompatible or if it's just the local scope addresses.

Thanks anyway for ready all this.
François.

---

### Post by glococo on 2011-07-28
Hi,

Same here, "showmount" and "mount" do not support IPv6.

Tried with "/srv/shared_resource *(rw,...." and nothing.

IPv6 should be a must in NFS.

Ping6 works fine.

Using Natty with "natty-proposed" sources enabled + Openwrt in Dir-825 + Fritzbox 7390. (all with IPv6)
ps: MysqlAdmin also not work with IPv6 Hosts. :(( grrr:(

---

### Post by ocwo92 on 2013-01-19
I realize this is an old post, but something caught my eye:

> **jæs said:**
> ```
/srv/partage    [fe80::225:22ff:fe06:b11c%eth0](rw,async,subtree_check,anonuid=1000,anongid=1000,all_squash)
```

According to [man exportfs](http://manpages.ubuntu.com/manpages/precise/man5/exports.5.html):

> IPv6 addresses must not be inside square brackets in  /etc/exports  lest they be confused with character-class wildcard matches.

So maybe it will work if you simply remove the square brackets.

---

