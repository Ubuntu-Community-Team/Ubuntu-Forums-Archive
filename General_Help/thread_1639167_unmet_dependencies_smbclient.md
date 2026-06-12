---
title: "unmet dependencies: smbclient"
date: 2010-12-06
forum: General Help
---

### Post by dimeotane on 2010-12-06
When I ran an upgrade yesterday the following error was shown:


```
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 smbclient : Depends: samba-common (= 2:3.5.4~dfsg-1ubuntu8) but 2:3.5.4~dfsg-1ubuntu8.1 is installed
E: Unmet dependencies. Try using -f.
```

I tried running the command $ sudo apt-get -f install and this came up:


```
The following packages will be upgraded:
  smbclient
1 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
Need to get 0B/13.6MB of archives.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 185853 files and directories currently installed.)
Preparing to replace smbclient 2:3.5.4~dfsg-1ubuntu8 (using .../smbclient_2%3a3.5.4~dfsg-1ubuntu8.1_i386.deb) ...
Unpacking replacement smbclient ...
dpkg-deb (subprocess): data: internal gzip read error: '<fd:0>: invalid stored block lengths'
dpkg-deb: subprocess <decompress> returned error exit status 2
dpkg: error processing /var/cache/apt/archives/smbclient_2%3a3.5.4~dfsg-1ubuntu8.1_i386.deb (--unpack):
 short read on buffer copy for backend dpkg-deb during `./usr/bin/smbcacls'
Errors were encountered while processing:
 /var/cache/apt/archives/smbclient_2%3a3.5.4~dfsg-1ubuntu8.1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Anyone also having this problem?  Anyone know how to fix it?

I tried redownloading this package "smbclient_2%3a3.5.4~dfsg-1ubuntu8.1_i386.deb", and tried to install it with Gdebi
but it said it can't continue until the broken package is fixed...

---

### Post by dimeotane on 2010-12-07
Ok, I think the problem is resolved now.

I came across [this page]("http://www.mydigitallife.info/2009/11/23/ubuntu-unmet-dependencies-not-going-to-be-installed-or-try-apt-get-f-install-error") where the command : "sudo apt-get autoclean" is recommended to fix the problem.

It worked for me.

---

### Post by CTolley on 2010-12-17
I had to use apt-get clean, but after running apt-get -f install again, the issue is resolved.  Thank you.

---

