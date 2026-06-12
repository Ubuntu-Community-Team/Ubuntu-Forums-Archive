---
title: "Terminating process if using high CPU usage for more than x seconds"
date: 2011-06-30
forum: General Help
---

### Post by fismtimesa on 2011-06-30
Is there any program to terminate process **[SIZE="3"]_automatically_[/SIZE]** if using more than 90% or 100% CPU time for more than 5 seconds? 
I have a program that opens a web browser, do some stuff on it and close it. But problem is that sometimes that browser starts using 100% CPU :confused:

Thank you.

---

### Post by Toz on 2011-06-30
Have a look at the program **monit**
```
$ apt-cache show monit
Package: monit
Priority: extra
Section: universe/admin
Installed-Size: 1056
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Stefan Alfredsson <alfs@debian.org>
Architecture: i386
Version: 1:5.2.1-1
Depends: libc6 (>= 2.11), libpam0g (>= 0.99.7.1), libssl0.9.8 (>= 0.9.8m-1)
Filename: pool/universe/m/monit/monit_5.2.1-1_i386.deb
Size: 493800
MD5sum: 5ccf2629da18532b0a6c0398b21d7815
SHA1: 40ddc1cb4c977bbeea8593209a3bd913e878e4f1
SHA256: c8efb95ad0c9319f820c81e77e62986b3bccf98f819a17bb19bd383820b90716
Description: A utility for monitoring and managing daemons or similar programs
 monit is a utility for monitoring and managing daemons or similar
 programs running on a Unix system. It will start specified programs
 if they are not running and restart programs not responding.
 .
 monit supports:
  * Daemon mode - poll programs at a specified interval
  * Monitoring modes - active, passive or manual
  * Start, stop and restart of programs
  * Group and manage groups of programs
  * Process dependency definition
  * Logging to syslog or own logfile
  * Configuration - comprehensive controlfile
  * Runtime and TCP/IP port checking (tcp and udp)
  * SSL support for port checking
  * Unix domain socket checking
  * Process status and process timeout
  * Process cpu usage
  * Process memory usage
  * Process zombie check
  * Check the systems load average
  * Check a file or directory timestamp
  * Alert, stop or restart a process based on its characteristics
  * MD5 checksum for programs started and stopped by monit
  * Alert notification for program timeout, restart, checksum, stop
    resource and timestamp error
  * Flexible and customizable email alert messages
  * Protocol verification. HTTP, FTP, SMTP, POP, IMAP, NNTP, SSH, DWP,
    LDAPv2 and LDAPv3
  * An http interface with optional SSL support to make monit
    accessible from a webbrowser
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Origin: Ubuntu

```

See also: [http://www.ubuntugeek.com/monitoring-ubuntu-services-using-monit.html]("http://www.ubuntugeek.com/monitoring-ubuntu-services-using-monit.html")

---

### Post by pqwoerituytrueiwoq on 2011-06-30
flash block or adblock plus could help with it (prevent reason to kill process)

---

