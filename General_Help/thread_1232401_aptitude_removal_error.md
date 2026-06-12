---
title: "aptitude removal error"
date: 2009-08-05
forum: General Help
---

### Post by adam35413 on 2009-08-05
I am trying to install updates, and I keep getting the following error when I do an sudo aptitude safe-upgrade:

```
The following packages are unused and will be REMOVED:
  ebox
The following packages will be upgraded:
  apache2 apache2-mpm-worker apache2-utils apache2.2-common bind9-host
  dhcp3-client dhcp3-common dnsutils libbind9-30 libdbus-1-3 libdns35 libgnutls13
  libisc35 libisccc30 libisccfg30 liblwres30 libparted1.7-1
  linux-image-2.6.24-24-server parted python2.5 python2.5-minimal samba
  samba-common smbclient smbfs
25 packages upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B/37.8MB of archives. After unpacking 2929kB will be freed.
Do you want to continue? [Y/n/?] y
Preconfiguring packages ...
(Reading database ... 27457 files and directories currently installed.)
Removing ebox ...
Can't locate Proc/ProcessTable.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.8.8 /usr/local/share/perl/5.8.8 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl .) at /usr/share/perl5/EBox/Module.pm line 23.
BEGIN failed--compilation aborted at /usr/share/perl5/EBox/Module.pm line 23.
Compilation failed in require at (eval 2) line 3.
        ...propagated at /usr/share/perl/5.8/base.pm line 84.
BEGIN failed--compilation aborted at /usr/share/perl5/EBox/GConfModule.pm line 21.
Compilation failed in require at (eval 1) line 3.
        ...propagated at /usr/share/perl/5.8/base.pm line 84.
BEGIN failed--compilation aborted at /usr/share/perl5/EBox/Global.pm line 21.
Compilation failed in require at /etc/init.d/ebox line 14.
BEGIN failed--compilation aborted at /etc/init.d/ebox line 14.
invoke-rc.d: initscript ebox, action "stop" failed.
/var/lib/dpkg/info/ebox.prerm: line 9: gconf-schemas: command not found
dpkg: error processing ebox (--remove):
 subprocess pre-removal script returned error exit status 127
Errors were encountered while processing:
 ebox
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done

```

What is the best way to fix this issue?

---

### Post by aysiu on 2009-08-06
Maybe this will help?
[http://translate.google.com/translate?u=http%3A%2F%2Fforum.webhostlist.de%2Fforum%2Fadministrations-und-verwaltungssoftware%2F33127-confixx-3-cant-locate-proc-processtable-pm.html&sl=de&tl=en&hl=en&ie=UTF-8](http://translate.google.com/translate?u=http%3A%2F%2Fforum.webhostlist.de%2Fforum%2Fadministrations-und-verwaltungssoftware%2F33127-confixx-3-cant-locate-proc-processtable-pm.html&sl=de&tl=en&hl=en&ie=UTF-8)

Not sure.

---

### Post by Soul-Sing on 2009-08-06
> dpkg: error processing ebox (--remove):
I think removing ebox doesn't stop the deamon. Somehow this has to be stopped.
Do you have ebox as a deamon running? (==>processen==>all processes)

---

### Post by adam35413 on 2009-08-06
leoquant: I did a process listing and grepped for ebox.  Nothing is running from ebox that I can see.

aysiu: I would install libproc-processtable-perl, but doing aptitude install libproc-processtable-perl breaks when aptitude tries to remove ebox first.  

Any more ideas?

---

