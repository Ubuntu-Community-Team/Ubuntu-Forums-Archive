---
title: "apt-get update not working"
date: 2006-02-08
forum: General Help
---

### Post by monkblah on 2006-02-08
Hi,

'sudo apt-get update' usually works for me, but for the past couple of days I have been getting error messages, like this:

```

...
Hit http://security.ubuntu.com breezy-security/universe Sources
Get:6 http://security.ubuntu.com breezy-security/main Packages [39.8kB]
99% [5 Packages gzip 0] [Connecting to archive.ubuntu.com] [Connecting to antes
gzip: stdin: not in gzip format
Err http://us.archive.ubuntu.com breezy/universe Packages
  Sub-process gzip returned an error code (1)
99% [6 Packages gzip 0] [Connecting to us.archive.ubuntu.com (216.165.129.138)]
gzip: stdin: not in gzip format
Err http://security.ubuntu.com breezy-security/main Packages
  Sub-process gzip returned an error code (1)
Get:7 http://us.archive.ubuntu.com breezy-updates/main Packages [31.3kB]
...
Hit http://kubuntu.org breezy/main Packages
Fetched 78.1kB in 16s (4717B/s)
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/breezy/universe/binary            -i386/Packages.gz  Sub-process gzip returned an error code (1)
Failed to fetch http://security.ubuntu.com/ubuntu/dists/breezy-security/main/bin            ary-i386/Packages.gz  Sub-process gzip returned an error code (1)
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used             instead.

```

Why am I getting these messages? Does this mean I cannot safely do an apt-get dist-upgrade?

---

### Post by dcstar on 2006-02-08
[QUOTE=monkblah]Hi,

'sudo apt-get update' usually works for me, but for the past couple of days I have been getting error messages, like this:
......
Why am I getting these messages? Does this mean I cannot safely do an apt-get dist-upgrade?[/QUOTE]
Possibly just problems with the us.archive server, you can try again later or edit your sources list to use another repository.

---

### Post by aysiu on 2006-02-08
See the first link of my signature.

---

### Post by monkblah on 2006-02-09
Thanks for the help!

---

