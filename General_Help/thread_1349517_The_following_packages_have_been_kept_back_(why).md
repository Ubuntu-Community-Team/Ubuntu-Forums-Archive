---
title: "The following packages have been kept back (why?)"
date: 2009-12-08
forum: General Help
---

### Post by alphaniner on 2009-12-08
I know kernel upgrades and related packages get held back with **apt-get upgrade**, but can anyone shed some light on why these packages were kept back:
```

  bind9-host dnsutils libbind9-40 libdns45 libisc45 libisccc40 libisccfg40
  liblwres40
```

Running 9.04 if it matters.

---

### Post by eugenevdm on 2009-12-09
I have a similar question, a little bit of Googling so far reveals they might be kept back because of compatibility problems, but the information is unclear.

---

### Post by KiLaHuRtZ on 2009-12-09
[https://answers.launchpad.net/ubuntu/+question/18330](https://answers.launchpad.net/ubuntu/+question/18330)

Most people don't use DNSSEC which is probably why they are "kept back" as the average user would not require them.

==========================================================
Ubuntu Security Notice USN-865-1          December 07, 2009
bind9 vulnerability
CVE-2009-4022
===========================================================

A security issue affects the following Ubuntu releases:

Ubuntu 6.06 LTS
Ubuntu 8.04 LTS
Ubuntu 8.10
Ubuntu 9.04
Ubuntu 9.10

This advisory also applies to the corresponding versions of
Kubuntu, Edubuntu, and Xubuntu.

The problem can be corrected by upgrading your system to the
following package versions:

Ubuntu 6.06 LTS:
  libdns23                        1:9.3.2-2ubuntu1.9

Ubuntu 8.04 LTS:
  libdns36                        1:9.4.2.dfsg.P2-2ubuntu0.4

Ubuntu 8.10:
  libdns44                        1:9.5.0.dfsg.P2-1ubuntu3.4

Ubuntu 9.04:
  libdns46                        1:9.5.1.dfsg.P2-1ubuntu0.3

Ubuntu 9.10:
  libdns53                        1:9.6.1.dfsg.P1-3ubuntu0.2

In general, a standard system upgrade is sufficient to effect the
necessary changes.

Details follow:

Michael Sinatra discovered that Bind did not correctly validate certain
records added to its cache. When DNSSEC validation is in use, a remote
attacker could exploit this to spoof DNS entries and poison DNS caches.
Among other things, this could lead to misdirected email and web traffic.

[...]

---

### Post by alphaniner on 2009-12-09
Thanks.

---

