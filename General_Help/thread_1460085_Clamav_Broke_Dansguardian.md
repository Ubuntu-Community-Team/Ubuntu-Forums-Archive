---
title: "Clamav Broke Dansguardian"
date: 2010-04-22
forum: General Help
---

### Post by ashkev on 2010-04-22
Hello,

I am running Dansguardian as part of the VMWARE Squid appliance,
Ubuntu, squid and Dansguardian.  It has been chugging along nicely for
over a year but now I get the following error whenever the system
reboots:

LibClamAV Error: cli_hex2str(): Malformed hexstring: This ClamAV
version has reached End of Life! Please upgrade to version 0.95 or
later. For more information see  [www.clamav.net/eol-clamav-094](www.clamav.net/eol-clamav-094) and
[www.clamav.net/download](www.clamav.net/download) (length: 169)
LibClamAV Error: Problem parsing signature at line 742
LibClamAV Error: Problem parsing database at line 742
LibClamAV Error: Can't load
/tmp/clamav-9ba10a5d231f3c06ca2ee0cc41ea0609/daily.ndb: Malformed
database
LibClamAV Error: Can't load /var/lib/clamav//daily.cvd: Malformed database
  ...fail!

I can get Dansguardian running by:

> rm /var/lib/clamav/daily.cvd
> /etc/init.d/clamav-freshclam stop
 * Stopping ClamAV virus database updater freshclam
  ...done.
> /etc/init.d/dansguardian restart
Restarting DansGuardian:  * Restarting DansGuardian:
  ...done.


I have tried uninstalling and reinstalling clamav, but to no avail.
How can I disable clamav, and let Dansguardian run without it?

Thanks,

Kevin Smith

---

### Post by eltorro on 2010-05-14
I've run into the same issue.

You can disable virus scanning by commenting the contentscanner line in /etc/dansguardian/dansguardian.conf.


I have not had time to investigate the cause.

---

