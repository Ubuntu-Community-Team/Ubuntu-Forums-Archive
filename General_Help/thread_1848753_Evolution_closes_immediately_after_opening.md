---
title: "Evolution closes immediately after opening"
date: 2011-09-23
forum: General Help
---

### Post by gdjartov on 2011-09-23
Regards to the fellow Linux community that is making the world a better place, one PC at the time.

Three days ago I left my computer running unattended for couple of hours after which my Evolution suddenly gave up on me - when I click on the icon it opens up for couple of seconds and then it opens the Bug Buddy saying "The application Evolution Mail crashed. The bug reporting tool was unable to collect enough information about the crash to be useful to the developers."
If I don't close the Bug Buddy I can still access Evolution and its preferences, but it doesn't send, nor receive e-mails. Closing Bug Buddy closes Evolution too. 

So far, I've reinstalled Evolution numerous times, including once with all the Add-ons. From another similar post, I've tried:

lsb_release -a; apt-cache policy evolution
LSB Version:    core-2.0-amd64:core-2.0-noarch:core-3.0-amd64:core-3.0-noarch:core-3.1-amd64:core-3.1-noarch:core-3.2-amd64:core-3.2-noarch:core-4.0-amd64:core-4.0-noarch
Distributor ID:    Ubuntu
Description:    Ubuntu 11.04
Release:    11.04
Codename:    natty
evolution:
  Installed: 2.32.2-0ubuntu7
  Candidate: 2.32.2-0ubuntu7
  Version table:
 *** 2.32.2-0ubuntu7 0
        500 [http://mn.archive.ubuntu.com/ubuntu/](http://mn.archive.ubuntu.com/ubuntu/) natty/main amd64 Packages
        100 /var/lib/dpkg/status

I've also ran sudo dpkg-reconfigure evolution, but I still Evolutionless.

---

### Post by dcstar on 2011-09-23
> **gdjartov said:**
> Regards to the fellow Linux community that is making the world a better place, one PC at the time.

Three days ago I left my computer running unattended for couple of hours after which my Evolution suddenly gave up on me - when I click on the icon it opens up for couple of seconds and then it opens the Bug Buddy saying "The application Evolution Mail crashed. The bug reporting tool was unable to collect enough information about the crash to be useful to the developers."
........

Run it from the command line and see what is output.

---

### Post by gdjartov on 2011-09-23
> **dcstar said:**
> Run it from the command line and see what is output.

georgi@GolfDeltaZulu:~$ evolution

(evolution:4803): GLib-GObject-CRITICAL **: Object class EMFolderTree doesn't implement property 'paste-target-list' from interface 'ESelectable'

(evolution:4803): GLib-GObject-CRITICAL **: Object class EMFolderTree doesn't implement property 'copy-target-list' from interface 'ESelectable'
Could not attach to process.  If your uid matches the uid of the target
process, check the setting of /proc/sys/kernel/yama/ptrace_scope, or try
again as the root user.  For more details, see /etc/sysctl.d/10-ptrace.conf
ptrace: Operation not permitted.
/home/georgi/4803: No such file or directory.
No stack.

:confused:

---

### Post by gdjartov on 2011-09-23
anyone?

---

### Post by gdjartov on 2011-09-24
Is it really so bad?

---

### Post by gdjartov on 2011-09-25
i guess this is an official bump, but I will give it a last chance

---

