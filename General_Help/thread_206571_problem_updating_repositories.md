---
title: "problem updating repositories"
date: 2006-06-30
forum: General Help
---

### Post by simone.brunozzi on 2006-06-30
Hi there,
I've a fresh ubuntu installed on a laptop; network is fine, I can ping the gateway and navigate the internet (and thus this forum too).

However, when I try to aptitude update, I have this unusual response:

```

root@ubuntu:/etc/apt# aptitude update
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
Err http://security.ubuntu.com dapper-security Release.gpg
  Connection failed
Err http://us.archive.ubuntu.com dapper Release.gpg
  Connection failed [IP: 146.137.96.15 80]
0% [Waiting for headers] [Waiting for headers]


```

Here I attach my sources.list file:

```

root@ubuntu:/etc/apt# cat sources.list

# Ubuntu 6.06 LTS (Canonical Ltd. Support)
deb http://us.archive.ubuntu.com/ubuntu/ dapper main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper main restricted

deb http://us.archive.ubuntu.com/ubuntu/ dapper-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper-updates main restricted

deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted

# Ubuntu Universe (Community Support)
deb http://us.archive.ubuntu.com/ubuntu/ dapper universe
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper universe

deb http://us.archive.ubuntu.com/ubuntu/ dapper-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper-updates universe

deb http://security.ubuntu.com/ubuntu dapper-security universe
deb-src http://security.ubuntu.com/ubuntu dapper-security universe

# Ubuntu Multiverse (Community Support)
deb http://us.archive.ubuntu.com/ubuntu/ dapper multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper multiverse

deb http://us.archive.ubuntu.com/ubuntu/ dapper-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper-updates multiverse

deb http://security.ubuntu.com/ubuntu dapper-security multiverse
deb-src http://security.ubuntu.com/ubuntu dapper-security multiverse


```

I think I have a problem with GPG keys... How can I solve it?

I also attach my /etc/apt/apt.conf file here:

```

root@ubuntu:/etc/apt# cat apt.conf
APT::Authentication::TrustCDROM "true";
Acquire::http::Proxy "false";


```

Thanks

---

