---
title: "logrotate error, 9.10"
date: 2010-06-04
forum: General Help
---

### Post by metalfan_ on 2010-06-04
hi,

i got some mail starting in the last days with this content:

```

/etc/cron.daily/logrotate:
error: bad top line in state file /var/lib/logrotate/status
error: could not read state file, will not attempt to write into it
run-parts: /etc/cron.daily/logrotate exited with return code 1

```

/var/lib/logrotate/status
```

Package: binutils-static
Auto-Installed: 1

Package: linux-restricted-modules-common
Auto-Installed: 1

Package: wireless-crda
Auto-Installed: 1

Package: python-support
Auto-Installed: 1

Package: iso-codes
Auto-Installed: 1

Package: libx11-data
Auto-Installed: 1

Package: python-apt
Auto-Installed: 1

Package: xml-core
Auto-Installed: 1

Package: libexpat1
Auto-Installed: 1

Package: libxcb1
Auto-Installed: 1

Package: libxau6
Auto-Installed: 1

Package: python-central
Auto-Installed: 1

Package: cron
Auto-Installed: 1

Package: libxdmcp6
Auto-Installed: 1

Package: libxml2
Auto-Installed: 1

Package: sgml-base
Auto-Installed: 1

Package: gettext-base
Auto-Installed: 1

Package: update-motd
Auto-Installed: 0

Package: python-gdbm
Auto-Installed: 1

Package: libx11-6
Auto-Installed: 1

Package: language-pack-en-base
Auto-Installed: 1

Package: grub-common
Auto-Installed: 1

Package: libwrap0
Auto-Installed: 1

Package: tcpd
Auto-Installed: 1

```

i have no clue what this is, i only installed packages via aptitude and did not modify anything logrotate related.
i will move the state file and report back tomorrow, maybe things improve.

---

### Post by DagMan on 2010-06-04
The second error might imply its a file permission problem.
I have 644 permissions for that file.

---

