---
title: "Who crashed my linux?!"
date: 2010-10-07
forum: General Help
---

### Post by zenon222 on 2010-10-07
I performed an update manager today.  Since then my box has locked-up three times.  A complete freeze unresponsive to any inputs.

-I'd like to rollback all updates performed in the last 24 hours, is this possible?
-Is there a known package causing this?
-What are my options?

I'm running Ubuntu studio 10.04 AMD-64

TIA.

---

### Post by gyussz on 2010-10-07
Have you tried running it in recovery mode? (You can try recovering broken packages, or run Ubuntu in failsafe X mode.)

---

### Post by DarthScape on 2010-10-07
Do you have any backups? Do you remember what updates they were? What application was running when it froze?

---

### Post by zenon222 on 2010-10-07
I found the log at  ```
/var/log/apt/term.log
```
the following packages were updated
```
Preparing to replace tzdata-java 2010l-0ubuntu0.10.04 (using .../tzdata-java_2010m-0ubuntu0.10.04_all.deb) ...
Preparing to replace tzdata 2010l-0ubuntu0.10.04 (using .../tzdata_2010m-0ubuntu0.10.04_all.deb) ...
Preparing to replace libdevmapper1.02.1 2:1.02.39-1ubuntu4 (using .../libdevmapper1.02.1_2%3a1.02.39-1ubuntu4.1_amd64.deb) ...
Preparing to replace mountall 2.15.2 (using .../mountall_2.15.3_amd64.deb) ...
Preparing to replace dmsetup 2:1.02.39-1ubuntu4 (using .../dmsetup_2%3a1.02.39-1ubuntu4.1_amd64.deb) ...
Preparing to replace libdevmapper-event1.02.1 2:1.02.39-1ubuntu4 (using .../libdevmapper-event1.02.1_2%3a1.02.39-1ubuntu4.1_amd64.deb) ...
Preparing to replace libpq-dev 8.4.4-0ubuntu10.04 (using .../libpq-dev_8.4.5-0ubuntu10.04_amd64.deb) ...
Preparing to replace libpq5 8.4.4-0ubuntu10.04 (using .../libpq5_8.4.5-0ubuntu10.04_amd64.deb) ...
Preparing to replace lvm2 2.02.54-1ubuntu4 (using .../lvm2_2.02.54-1ubuntu4.1_amd64.deb) ...
Preparing to replace openssl 0.9.8k-7ubuntu8.2 (using .../openssl_0.9.8k-7ubuntu8.3_amd64.deb) ...
```
Ideas?

---

