---
title: "Ubuntu crashed unexpectedly with PackageKit errors..."
date: 2012-05-26
forum: General Help
---

### Post by etdsbastar on 2012-05-26
Hello friends,

I got these errors and a serious system crash after a successful update of my ubuntu machine today:

```
May 27 01:25:14 ... kernel: [18469.963172] unity-panel-ser[6476]: segfault at 61746179 ip 0804d0b2 sp bf96e810 error 4 in unity-panel-service[8048000+e000]
May 27 01:26:24 ... dbus[798]: [system] Activating service name='org.freedesktop.PackageKit' (using servicehelper)
May 27 01:26:25 ... AptDaemon: INFO: Initializing daemon
May 27 01:26:25 ... AptDaemon.PackageKit: INFO: Initializing PackageKit compat layer
May 27 01:26:25 ... dbus[798]: [system] Successfully activated service 'org.freedesktop.PackageKit'
May 27 01:26:25 ... AptDaemon.PackageKit: INFO: Initializing PackageKit transaction
May 27 01:26:25 ... AptDaemon.Worker: INFO: Simulating trans: /org/debian/apt/transaction/ea839f65dba14cd8a1e60d2c3ff2dc6d
May 27 01:26:25 ... AptDaemon.Worker: INFO: Processing transaction /org/debian/apt/transaction/ea839f65dba14cd8a1e60d2c3ff2dc6d
May 27 01:26:27 ... AptDaemon.PackageKit: INFO: Get updates()
May 27 01:26:27 ... AptDaemon.Worker: INFO: Finished transaction /org/debian/apt/transaction/ea839f65dba14cd8a1e60d2c3ff2dc6d
May 27 01:32:25 ... AptDaemon: INFO: Quitting due to inactivity
May 27 01:32:25 ... AptDaemon: INFO: Quitting was requested

```Please help.

---

### Post by etdsbastar on 2012-05-30
Is there anyone who can help me please...

---

