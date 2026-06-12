---
title: "[launchpad] fail to upload to my PPA, showing [Errno 111] Connection refused"
date: 2009-10-28
forum: General Help
---

### Post by cheeselee on 2009-10-28
Anybody can help me?

```
cheese@cheese-laptop:~/build/mentohust$ LANG=en_US.UTF8 dput my-ppa mentohust_0.2.4-0~ppa1_source.changes
Checking Signature on .changes
gpg: Signature made Tue Oct 27 22:05:45 2009 CST using DSA key ID 294F35F9
gpg: Good signature from "Cheese Lee <cheeselee@126.com>"
Good signature on /home/cheese/build/mentohust/mentohust_0.2.4-0~ppa1_source.changes.
Checking Signature on .dsc
gpg: Signature made Tue Oct 27 22:05:42 2009 CST using DSA key ID 294F35F9
gpg: Good signature from "Cheese Lee <cheeselee@126.com>"
Good signature on /home/cheese/build/mentohust/mentohust_0.2.4-0~ppa1.dsc.
Package includes an .orig.tar.gz file although the debian revision suggests
that it might not be required. Multiple uploads of the .orig.tar.gz may be
rejected by the upload queue management software.
Uploading to my-ppa (via ftp to ppa.launchpad.net):
  Uploading mentohust_0.2.4-0~ppa1.dsc: [Errno 111] Connection refused
```
```
cheese@cheese-laptop:~$ ping -c 3 ppa.launchpad.net
PING ppa.launchpad.net (91.189.90.217) 56(84) bytes of data.
64 bytes from germanium.canonical.com (91.189.90.217): icmp_seq=1 ttl=39 time=649 ms
64 bytes from germanium.canonical.com (91.189.90.217): icmp_seq=2 ttl=39 time=653 ms
64 bytes from germanium.canonical.com (91.189.90.217): icmp_seq=3 ttl=39 time=647 ms

--- ppa.launchpad.net ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 1999ms
rtt min/avg/max/mdev = 647.343/650.159/653.467/2.690 ms

```

```

cheese@cheese-laptop:~$ cat /home/cheese/.dput.cf
[my-ppa]
fqdn = ppa.launchpad.net
method = ftp
incoming = ~cheeselee/ppa/ubuntu/
login = anonymous

```

---

### Post by opengonzo on 2010-02-28
same problem.......

all ok 10 minutes ago, but now error 111

---

### Post by www.rzr.online.fr on 2010-05-09
hi

upload works for me , but i dont see my files on LP , and did not get confirmation email

-- 
[http://rzr.online.fr/q/build](http://rzr.online.fr/q/build)

---

