---
title: "I can't install AVG, says package is of bad quality"
date: 2011-09-19
forum: General Help
---

### Post by JMatt40 on 2011-09-19
I just installed ubuntu and have been trying to install AVG for a while now, I tried the code in the terminal thing and that didn't work, now I am trying to install it from the AVG site and it says: The package is of bad quality. The installation of a package which violates the quality standards isn't allowed. This could cause serious problems on your computer. Please contact the person or organization who provided this package file and include the details beneath. 

This it shows this: Lintian check results for /tmp/avg85flx-r874-a3473.i386.deb:
```
E: avg85flx: wrong-file-owner-uid-or-gid opt/avg/ 1008/407 
E: avg85flx: wrong-file-owner-uid-or-gid opt/avg/avg8/ 1008/407 
E: avg85flx: wrong-file-owner-uid-or-gid opt/avg/avg8/bin/ 1008/407 
E: avg85flx: wrong-file-owner-uid-or-gid opt/avg/avg8/bin/avgavid 1008/407 
E: avg85flx: wrong-file-owner-uid-or-gid opt/avg/avg8/bin/avgcfgctl 1008/407 
E: avg85flx: wrong-file-owner-uid-or-gid opt/avg/avg8/bin/avgctl 1008/407 
E: avg85flx: wrong-file-owner-uid-or-gid opt/avg/avg8/bin/avgd 1008/407 
E: avg85flx: wrong-file-owner-uid-or-gid opt/avg/avg8/bin/avgdiag.sh 1008/407 
E: avg85flx: wrong-file-owner-uid-or-gid opt/avg/avg8/bin/avgdump 1008/407 
E: avg85flx: wrong-file-owner-uid-or-gid opt/avg/avg8/bin/avgoad 1008/407 
E: avg85flx: wrong-file-owner-uid-or-gid opt/avg/avg8/bin/avgscan 1008/407 
E: avg85flx: wrong-file-owner-uid-or-gid opt/avg/avg8/bin/avgscand 1008/407 
E: avg85flx: wrong-file-owner-uid-or-gid opt/avg/avg8/bin/avgsched 1008/407 
E: avg85flx: wrong-file-owner-uid-or-gid opt/avg/avg8/bin/avgspamd 1008/407 
E: avg85flx: wrong-file-owner-uid-or-gid opt/avg/avg8/bin/avgtcpd 1008/407 
E: avg85flx: wrong-file-owner-uid-or-gid opt/avg/avg8/bin/avgupd 1008/407 
E: avg85flx: wrong-file-owner-uid-or-gid opt/avg/avg8/bin/avgupdate 1008/407 
E: avg85flx: wrong-file-owner-uid-or-gid opt/avg/avg8/bin/avgwrapper.sh 1008/407 
E: avg85flx: wrong-file-owner-uid-or-gid opt/avg/avg8/cfg/ 1008/407 
E: avg85flx: wrong-file-owner-uid-or-gid opt/avg/avg8/cfg/dfncfg.dat 1008/407 
E: avg85flx: wrong-file-owner-uid-or-gid opt/avg/avg8/doc/ 1008/407 
E: avg85flx: wrong-file-owner-uid-or-gid opt/avg/avg8/doc/ChangeLog 1008/407 
E: avg85flx: wrong-file-owner-uid-or-gid opt/avg/avg8/doc/README 1008/407 
E: avg85flx: wrong-file-owner-uid-or-gid opt/avg/avg8/doc/README.amavis 1008/407 
E: avg85flx: wrong-file-owner-uid-or-gid opt/avg/avg8/doc/README.exim 1008/407 
E: avg85flx: wrong-file-owner-uid-or-gid opt/avg/avg8/doc/README.postfix 1008/407 
E: avg85flx: wrong-file-owner-uid-or-gid opt/avg/avg8/doc/README.qmail 1008/407 
E: avg85flx: wrong-file-owner-uid-or-gid opt/avg/avg8/doc/README.qmailscanner 1008/407 
E: avg85flx: wrong-file-owner-uid-or-gid opt/avg/avg8/doc/README.sendmail 1008/407 
E: avg85flx: wrong-file-owner-uid-or-gid opt/avg/avg8/doc/licenses/ 1008/407 
E: avg85flx: wrong-file-owner-uid-or-gid opt/avg/avg8/doc/licenses/7zip.txt 1008/407 
E: avg85flx: wrong-file-owner-uid-or-gid opt/avg/avg8/doc/licenses/ace.txt 1008/407 
E: avg85flx: wrong-file-owner-uid-or-gid opt/avg/avg8/doc/licenses/arabica.txt 1008/407 
E: avg85flx: wrong-file-owner-uid-or-gid opt/avg/avg8/doc/licenses/boost.txt 1008/407 
E: avg85flx: wrong-file-owner-uid-or-gid opt/avg/avg8/doc/licenses/bsdiff.txt 1008/407 
E: avg85flx: wrong-file-owner-uid-or-gid opt/avg/avg8/doc/licenses/bzip.txt 1008/407 
E: avg85flx: wrong-file-owner-uid-or-gid opt/avg/avg8/doc/licenses/carp.html 1008/407 
E: avg85flx: wrong-file-owner-uid-or-gid opt/avg/avg8/doc/licenses/cryptopp.txt 1008/407 
E: avg85flx: wrong-file-owner-uid-or-gid opt/avg/avg8/doc/licenses/curl.txt 1008/407 
E: avg85flx: wrong-file-owner-uid-or-gid opt/avg/avg8/doc/licenses/dazukofs.txt 1008/407 
E: avg85flx: wrong-file-owner-uid-or-gid opt/avg/avg8/doc/licenses/expat.txt 1008/407 
E: avg85flx: wrong-file-owner-uid-or-gid opt/avg/avg8/doc/licenses/imagemagick.txt 1008/407 
E: avg85flx: wrong-file-owner-uid-or-gid opt/avg/avg8/doc/licenses/infozip.txt 1008/407 
E: avg85flx: wrong-file-owner-uid-or-gid opt/avg/avg8/doc/licenses/lua.txt 1008/407 
E: avg85flx: wrong-file-owner-uid-or-gid opt/avg/avg8/doc/licenses/md4_md5_license.txt 1008/407 
E: avg85flx: wrong-file-owner-uid-or-gid opt/avg/avg8/doc/licenses/milter.txt 1008/407 
E: avg85flx: wrong-file-owner-uid-or-gid opt/avg/avg8/doc/licenses/minizip.txt 1008/407 
E: avg85flx: wrong-file-owner-uid-or-gid opt/avg/avg8/doc/licenses/openssl_license.html 1008/407 
E: avg85flx: wrong-file-owner-uid-or-gid opt/avg/avg8/doc/licenses/sasl.txt 1008/407 
E: avg85flx: wrong-file-owner-uid-or-gid opt/avg/avg8/doc/licenses/tinyxml.txt 1008/407 
E: avg85flx: wrong-file-owner-uid-or-gid opt/avg/avg8/doc/licenses/unrar.txt 1008/407 
E: avg85flx: wrong-file-owner-uid-or-gid opt/avg/avg8/doc/licenses/untar.txt 1008/407 
E: avg85flx: wrong-file-owner-uid-or-gid opt/avg/avg8/doc/licenses/xalan_xerces.txt 1008/407 
E: avg85flx: wrong-file-owner-uid-or-gid opt/avg/avg8/doc/licenses/zlib.txt 1008/407 
E: avg85flx: wrong-file-owner-uid-or-gid opt/avg/avg8/etc/ 1008/407 
E: avg85flx: wrong-file-owner-uid-or-gid opt/avg/avg8/etc/avg.conf 1008/407 
E: avg85flx: wrong-file-owner-uid-or-gid opt/avg/avg8/etc/init.d/ 1008/407 
E: avg85flx: wrong-file-owner-uid-or-gid opt/avg/avg8/etc/init.d/avgd.all 1008/407 
E: avg85flx: wrong-file-owner-uid-or-gid opt/avg/avg8/etc/init.d/avgd.gentoo 1008/407 
E: avg85flx: wrong-file-owner-uid-or-gid opt/avg/avg8/etc/init.d/avgdinit.conf 1008/407 
E: avg85flx: wrong-file-owner-uid-or-gid opt/avg/avg8/etc/init.d/functions.common 1008/407 
E: avg85flx: wrong-file-owner-uid-or-gid opt/avg/avg8/etc/init.d/functions.deb 1008/407 
E: avg85flx: wrong-file-owner-uid-or-gid opt/avg/avg8/etc/init.d/functions.diag 1008/407 
E: avg85flx: wrong-file-owner-uid-or-gid opt/avg/avg8/etc/init.d/functions.freebsd 1008/407 
E: avg85flx: wrong-file-owner-uid-or-gid opt/avg/avg8/etc/init.d/functions.gentoo 1008/407 
E: avg85flx: wrong-file-owner-uid-or-gid opt/avg/avg8/etc/init.d/functions.mdk 1008/407 
E: avg85flx: wrong-file-owner-uid-or-gid opt/avg/avg8/etc/init.d/functions.rh 1008/407 
E: avg85flx: wrong-file-owner-uid-or-gid opt/avg/avg8/etc/init.d/functions.slack 1008/407 
E: avg85flx: wrong-file-owner-uid-or-gid opt/avg/avg8/etc/init.d/functions.suse 1008/407 
E: avg85flx: wrong-file-owner-uid-or-gid opt/avg/avg8/etc/init.d/functions.ubuntu 1008/407 
E: avg85flx: wrong-file-owner-uid-or-gid opt/avg/avg8/lib/ 1008/407 
E: avg85flx: wrong-file-owner-uid-or-gid opt/avg/avg8/lib/libavgaspam.so 1008/407 
E: avg85flx: wrong-file-owner-uid-or-gid opt/avg/avg8/lib/libavgcert.so 1008/407 
E: avg85flx: wrong-file-owner-uid-or-gid opt/avg/avg8/lib/libavgcfg.so 1008/407 
E: avg85flx: wrong-file-owner-uid-or-gid opt/avg/avg8/lib/libavgcore.so 1007/100 
E: avg85flx: wrong-file-owner-uid-or-gid opt/avg/avg8/lib/libavginet.so 1008/407 
E: avg85flx: wrong-file-owner-uid-or-gid opt/avg/avg8/lib/libavglng.so 1008/407 
E: avg85flx: wrong-file-owner-uid-or-gid opt/avg/avg8/lib/libavglogd.so 1008/407 
E: avg85flx: wrong-file-owner-uid-or-gid opt/avg/avg8/lib/libavgupd.so 1008/407 
E: avg85flx: wrong-file-owner-uid-or-gid opt/avg/avg8/lib/libdazukofs.so 1008/407 
E: avg85flx: wrong-file-owner-uid-or-gid opt/avg/avg8/lib/libgcc_s.so.1 1008/407 
E: avg85flx: wrong-file-owner-uid-or-gid opt/avg/avg8/lib/libspamcatcher.so 1008/407 
E: avg85flx: wrong-file-owner-uid-or-gid opt/avg/avg8/lib/libstdc++.so.6 1008/407 
E: avg85flx: wrong-file-owner-uid-or-gid opt/avg/avg8/log/ 1008/407 
E: avg85flx: wrong-file-owner-uid-or-gid opt/avg/avg8/man/ 1008/407 
E: avg85flx: wrong-file-owner-uid-or-gid opt/avg/avg8/man/man1/ 1008/407 
E: avg85flx: wrong-file-owner-uid-or-gid opt/avg/avg8/man/man1/avgavid.1.gz 1008/407 
E: avg85flx: wrong-file-owner-uid-or-gid opt/avg/avg8/man/man1/avgcfgctl.1.gz 1008/407 
E: avg85flx: wrong-file-owner-uid-or-gid opt/avg/avg8/man/man1/avgctl.1.gz 1008/407 
E: avg85flx: wrong-file-owner-uid-or-gid opt/avg/avg8/man/man1/avgd.1.gz 1008/407 
E: avg85flx: wrong-file-owner-uid-or-gid opt/avg/avg8/man/man1/avgdump.1.gz 1008/407 
E: avg85flx: wrong-file-owner-uid-or-gid opt/avg/avg8/man/man1/avgoad.1.gz 1008/407 
E: avg85flx: wrong-file-owner-uid-or-gid opt/avg/avg8/man/man1/avgscan.1.gz 1008/407 
E: avg85flx: wrong-file-owner-uid-or-gid opt/avg/avg8/man/man1/avgscand.1.gz 1008/407 
E: avg85flx: wrong-file-owner-uid-or-gid opt/avg/avg8/man/man1/avgsched.1.gz 1008/407 
E: avg85flx: wrong-file-owner-uid-or-gid opt/avg/avg8/man/man1/avgspamd.1.gz 1008/407 
E: avg85flx: wrong-file-owner-uid-or-gid opt/avg/avg8/man/man1/avgtcpd.1.gz 1008/407 
E: avg85flx: wrong-file-owner-uid-or-gid opt/avg/avg8/man/man1/avgupd.1.gz 1008/407 
E: avg85flx: wrong-file-owner-uid-or-gid opt/avg/avg8/man/man1/avgupdate.1.gz 1008/407 
E: avg85flx: wrong-file-owner-uid-or-gid opt/avg/avg8/update/ 1008/407 
E: avg85flx: wrong-file-owner-uid-or-gid opt/avg/avg8/var/ 1008/407 
E: avg85flx: wrong-file-owner-uid-or-gid opt/avg/avg8/var/antispam/ 1008/407 
E: avg85flx: wrong-file-owner-uid-or-gid opt/avg/avg8/var/antispam/approvedsenders 1008/407 
E: avg85flx: wrong-file-owner-uid-or-gid opt/avg/avg8/var/antispam/blockedsenders 1008/407 
E: avg85flx: wrong-file-owner-uid-or-gid opt/avg/avg8/var/antispam/sc1.bin.full 1008/407 
E: avg85flx: wrong-file-owner-uid-or-gid opt/avg/avg8/var/antispam/sc10.bin.full 1008/407 
E: avg85flx: wrong-file-owner-uid-or-gid opt/avg/avg8/var/antispam/sc11.bin.full 1008/407 
E: avg85flx: wrong-file-owner-uid-or-gid opt/avg/avg8/var/antispam/sc12.bin.full 1008/407 
E: avg85flx: wrong-file-owner-uid-or-gid opt/avg/avg8/var/antispam/sc14.bin.full 1008/407 
E: avg85flx: wrong-file-owner-uid-or-gid opt/avg/avg8/var/antispam/sc2.bin.full 1008/407 
E: avg85flx: wrong-file-owner-uid-or-gid opt/avg/avg8/var/antispam/sc5.bin.full 1008/407 
E: avg85flx: wrong-file-owner-uid-or-gid opt/avg/avg8/var/antispam/sc6.bin.full 1008/407 
E: avg85flx: wrong-file-owner-uid-or-gid opt/avg/avg8/var/antispam/sc9.bin.full 1008/407 
E: avg85flx: wrong-file-owner-uid-or-gid opt/avg/avg8/var/antispam/scbin.txt 1008/407 
E: avg85flx: wrong-file-owner-uid-or-gid opt/avg/avg8/var/antispam/spamcatcher.conf 1008/407 
E: avg85flx: wrong-file-owner-uid-or-gid opt/avg/avg8/var/data/ 1008/407 
E: avg85flx: wrong-file-owner-uid-or-gid opt/avg/avg8/var/data/avg8us.lng 1008/407 
E: avg85flx: wrong-file-owner-uid-or-gid opt/avg/avg8/var/data/incavi.avm 1008/407 
E: avg85flx: wrong-file-owner-uid-or-gid opt/avg/avg8/var/run/ 1008/407 
E: avg85flx: arch-independent-package-contains-binary-or-object opt/avg/avg8/bin/avgavid 
E: avg85flx: arch-independent-package-contains-binary-or-object opt/avg/avg8/bin/avgcfgctl 
E: avg85flx: arch-independent-package-contains-binary-or-object opt/avg/avg8/bin/avgctl 
E: avg85flx: arch-independent-package-contains-binary-or-object opt/avg/avg8/bin/avgd 
E: avg85flx: arch-independent-package-contains-binary-or-object opt/avg/avg8/bin/avgdump 
E: avg85flx: arch-independent-package-contains-binary-or-object opt/avg/avg8/bin/avgoad 
E: avg85flx: arch-independent-package-contains-binary-or-object opt/avg/avg8/bin/avgscan 
E: avg85flx: arch-independent-package-contains-binary-or-object opt/avg/avg8/bin/avgscand 
E: avg85flx: arch-independent-package-contains-binary-or-object opt/avg/avg8/bin/avgsched 
E: avg85flx: arch-independent-package-contains-binary-or-object opt/avg/avg8/bin/avgspamd 
E: avg85flx: arch-independent-package-contains-binary-or-object opt/avg/avg8/bin/avgtcpd 
E: avg85flx: arch-independent-package-contains-binary-or-object opt/avg/avg8/bin/avgupd 
E: avg85flx: arch-independent-package-contains-binary-or-object opt/avg/avg8/bin/avgupdate 
E: avg85flx: arch-independent-package-contains-binary-or-object opt/avg/avg8/lib/libavgaspam.so 
E: avg85flx: arch-independent-package-contains-binary-or-object opt/avg/avg8/lib/libavgcert.so 
E: avg85flx: arch-independent-package-contains-binary-or-object opt/avg/avg8/lib/libavgcfg.so 
E: avg85flx: arch-independent-package-contains-binary-or-object opt/avg/avg8/lib/libavgcore.so 
E: avg85flx: arch-independent-package-contains-binary-or-object opt/avg/avg8/lib/libavginet.so 
E: avg85flx: arch-independent-package-contains-binary-or-object opt/avg/avg8/lib/libavglng.so 
E: avg85flx: arch-independent-package-contains-binary-or-object opt/avg/avg8/lib/libavglogd.so 
E: avg85flx: arch-independent-package-contains-binary-or-object opt/avg/avg8/lib/libavgupd.so 
E: avg85flx: arch-independent-package-contains-binary-or-object opt/avg/avg8/lib/libdazukofs.so 
E: avg85flx: arch-independent-package-contains-binary-or-object opt/avg/avg8/lib/libgcc_s.so.1 
E: avg85flx: arch-independent-package-contains-binary-or-object opt/avg/avg8/lib/libspamcatcher.so 
E: avg85flx: arch-independent-package-contains-binary-or-object opt/avg/avg8/lib/libstdc++.so.6
```

---

### Post by seawolf167 on 2011-09-19
Looks like this is a AVG [bug]("http://forums.avg.com/us-en/avg-forums?sec=thread&act=show&id=166037"). The file is a .deb file, so you should be able to double click it to install it.

A good alternative is [clamav]("https://help.ubuntu.com/community/ClamAV").

---

### Post by howefield on 2011-09-19
Just wanted to mention seeing as you are new, AVG for linux doesn't come with a GUI, it is command line driven. Apologies if you already knew that.

Again, just in case you weren't aware, there aren't that many reasons for running anti virus in linux, most are outlined here...

[https://help.ubuntu.com/community/Antivirus](https://help.ubuntu.com/community/Antivirus)

---

### Post by JMatt40 on 2011-09-19
@seawolf167: I got that clam program, thanks :D 

@howefield: Yeah I know but I kind of want an anti virus program so I can feel a little safer. Is there a need for me to change settings around in the firewall by the way?? 

I also just got an update manager pop up box and it shows theres 237 updates to install and theres a bunch of random things, should I install them all?

---

### Post by seawolf167 on 2011-09-19
> **JMatt40 said:**
> Is there a need for me to change settings around in the firewall by the way??

There is no firewall enabled by default in Ubuntu. If you want to run one but don't want to manually edit your iptables, a good graphical front end is

```
sudo apt-get install gufw
```

> **JMatt40 said:**
> I also just got an update manager pop up box and it shows theres 237 updates to install and theres a bunch of random things, should I install them all?

These are generally bug fixes and security patches and should be installed. You can install them via the popup, or to manually check and install use the following command

```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by JMatt40 on 2011-09-19
> **seawolf167 said:**
> There is no firewall enabled by default in Ubuntu. If you want to run one but don't want to manually edit your iptables, a good graphical front end is

```
sudo apt-get install gufw
```

These are generally bug fixes and security patches and should be installed. You can install them via the popup, or to manually check and install use the following command

```
sudo apt-get update
sudo apt-get upgrade
```

Ok I'm now at the firewall configuration, I just searched for gufw because I can't get the terminal thing to work right and it shows I can click enabled and click incoming and outgoing, so what should I click if anything at all?

---

### Post by seawolf167 on 2011-09-19
Unless you have a specific reason too, you don't need to enable a firewall on your computer as a default install shouldn't have any open ports. If you want to go ahead anyways, you'll want to "poke holes" in the firewall for any services you are using (like SSH, HTTP, etc.)

---

