---
title: "Help"
date: 2010-12-18
forum: General Help
---

### Post by lotten on 2010-12-18
Hi

 Do not know if this is right place to ask for help, but both Ubuntu and the forum is new to me. Have a computer with ubuntu, but it has been a whole year without being used. Now when I turn it on I get this message:

 * An automatic filesystem check (fsck) of the root file system failed. A manual fsck must ask Performed, simply the system restarted. The fsck Hubble ask Performed in maintenance mode with the root file system mounted in read-only.

 * The root filesystem is mounted Currently in read-only mode. A maintenance shell goodwill now be started. After performing system maintance, press Control-D two terminate the maintenance shell and restart the system.
 bash: no job control in this shell

 root@mbuno- laptop:¨#

Dont know what to do, is it hope for my computer?

Lotte

---

### Post by sikander3786 on 2010-12-18
Welcome to the forums :-)

From the same commandline, run fsck this way.

```
fsck -F file_system_type partition
```

If that doesn't succeed either, boot an Ubuntu Live CD/USB and perform fsck from there.

[https://help.ubuntu.com/community/SystemAdministration/Fsck](https://help.ubuntu.com/community/SystemAdministration/Fsck)

---

