---
title: "Areca controller and smartmontools"
date: 2009-11-05
forum: General Help
---

### Post by zuehls on 2009-11-05
I have installed Ubuntu 9.10 and am trying to get smartmontools working with an areca card (1210).  The sourceforge site for smartmontools says that areca is supported ([http://sourceforge.net/apps/trac/smartmontools/wiki/Supported_RAID-Controllers](http://sourceforge.net/apps/trac/smartmontools/wiki/Supported_RAID-Controllers)).  I have firmware 1.47 installed but I cannot seem to get it to work.

When I run: sudo smartctl -a -d areca,4 /dev/sg1

I get an error saying I am using -d incorrectly...
VALID ARGUMENTS ARE: ata, scsi, marvell, sat, 3ware,N, hpt,L/M/N cciss,N


Anyone get this to work???

---

### Post by alphaniner on 2009-11-05
Are you sure the version of smartctl you are using is the same described on sourceforge?  You can get the version by using **smartctl -V**.  You could also search the manpage when it is open by typing / followed by your search string (ie. **/areca**) and hitting Enter.  You can continue the search by simply typing / and Enter.

---

### Post by zuehls on 2009-11-05
I have the version of smartctl from default Ubuntu 9.10 repositories.  When I run smartctl -V I get:

smartmontools release 5.38 dated 2008/03/10 at 10:44:07 GMT
smartmontools build host: i686-pc-linux-gnu
smartmontools build configured: 2009/10/07 14:06:17 UTC
smartctl compile dated Oct  7 2009 at 14:06:34
smartmontools configure arguments:  '--prefix=/usr' '--sysconfdir=/etc' '--mandir=/usr/share/man' '--with-initscriptdir=/etc/init.d' '--with-docdir=/usr/share/doc/smartmontools' 'CXXFLAGS=-g -O2' 'LDFLAGS=-Wl,-Bsymbolic-functions' 'CPPFLAGS=' 'CFLAGS=-fsigned-char -Wall -O2'

---

### Post by alphaniner on 2009-11-05
That seems to be the current version.  I dunno what to tell ya.  I have access to Areca controllers at work, if you don't figure anything out I may be able to give it a shot tomorrow.

---

### Post by zuehls on 2009-11-05
Please do try it at work.  I had Ubuntu 8.10 installed before 9.10 and had the same issue...that being smartctl did not appear to offer ability to see disks behind areca card.

thx

---

### Post by alphaniner on 2009-11-06
I booted to a 9.04 LiveCD and installed smartmontools from the repositories.  I got the same error as you.  I searched the man page and the word areca was not found, meaning that whatever version we are using, it does not correspond to the version described by the [online man page]("http://smartmontools.sourceforge.net/man/smartctl.8.html").

I also just noticed the date of the package from your **smartctl -V** output: 2008/03/10.  Mine is the same.  According to the supported devices page, "Areca support on Linux added at 2008-07-24."  That would seem to clinch it.  The version in the repos predates Areca support.

However, the confusing thing is that v5.38 really is the most recent stable release; even the source package is v5.38 and dated 2008.03.10.  I guess this means that Areca support only exists in an unreleased version, which can only be [downloaded as source through SVN]("http://sourceforge.net/apps/trac/smartmontools/wiki/Download#InstalllatestunreleasedcodefromSVNrepository").

---

### Post by zuehls on 2009-11-06
Thx for all your help...guess I'll have to get it from SVN and try.

---

