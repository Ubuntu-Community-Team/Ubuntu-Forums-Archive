---
title: "atd file in wrong format"
date: 2010-09-15
forum: General Help
---

### Post by karlatsaic on 2010-09-15
I have a problem with the at daemon (atd). My syslog is full of messages like:

Sep 14 08:34:52 khr-laptop-local atd[6866]: File a02a2701466b93 is in wrong format - aborting
Sep 14 08:34:52 khr-laptop-local atd[6868]: File a01ad4013f05c0 is in wrong format - aborting
Sep 14 08:34:52 khr-laptop-local atd[6884]: File a02a2701466b93 is in wrong format - aborting
Sep 14 08:34:52 khr-laptop-local atd[6871]: File a01ad1013f05b8 is in wrong format - aborting
Sep 14 08:34:52 khr-laptop-local atd[6888]: File a01ad0013f05b6 is in wrong format - aborting

A few occasional messages would be OK, but these are coming so rapidly, my filesystem filled up and brought everything to a screeching halt. I ran 'sudo service atd stop' and cleaned out 44 GB of syslog garbage and everything is OK. At the moment, it looks like I need to stop atd every time I reboot. A colleague, also running 10.04 is experiencing the same symptoms and he was the one who advised me to simply stop atd on every reboot. Is this happening for others?

I am not only running 10.04 LTS, but also have a fully encrypted drive (which was created with ubuntu 8.04 LTS alternate installation iso). Perhaps the drive encryption is getting in the way, but everything else works perfectly as far as I can tell.

---

### Post by gmargo on 2010-09-15
**at** stores it's future work in the **/var/spool/cron/atjobs/** directory.  Check that directory for these offending files.

---

### Post by karlatsaic on 2010-09-15
Thanks for the tip. It looked dangerous to actually touch the files in there. Some of them were a couple weeks old and atq showed jobs running. I'm hoping those were the offending files. Rather than simply trying to delete those files, I just executed atrm on all the processes in my atq. This cleaned out all the files and, hopefully, solved the problem. I'll keep monitoring.

---

