---
title: "Preferences of mirror in aptitude (or apt-get)"
date: 2011-04-17
forum: General Help
---

### Post by wimille on 2011-04-17
Hello,

I've a local mirror of Ubuntu repository (for Natty) on my server. 

On my main PC i want to use this mirror, so i edit my sources.list and i add the following lines :
```

deb http://walter/ubuntu natty main restricted universe multiverse

```When i update the packages list, i've no problems. 

But what i want is to give priority to my local mirror than to distant mirror. So i create /etc/apt/preferences file and i wrote :
```

Package: *
Pin: origin walter
Pin-Priority: 600

Package: *
Pin: origin "ubuntu-archive.mirrors.proxad.net"
Pin-Priority: 400

```When i do apt-cache policy, i've correct priority.

But when i try to install some packages, they are downloaded from internet and not from y local server.

If anyone can help me, thanks.

---

