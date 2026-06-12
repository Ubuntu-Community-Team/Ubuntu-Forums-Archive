---
title: "update manager not working"
date: 2012-06-18
forum: General Help
---

### Post by qianming on 2012-06-18
when i open up update manager,it shows "Could not initialize the package information"
the detail is:
An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_precise-security_universe_i18n_Translation-en, E:The package lists or status file could not be parsed or opened.'

when i open the file :"/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_precise-security_universe_i18n_Translation-en"
it shows:<html><head><script language=javascript>location='http://172.16.2.14/muxjp.php?2539437403'</script></head></html>

what can i do about it?please help,great thanks!!

---

### Post by plucky on 2012-06-18
> **qianming said:**
> when i open up update manager,it shows "Could not initialize the package information"
the detail is:
An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_precise-security_universe_i18n_Translation-en, E:The package lists or status file could not be parsed or opened.'

when i open the file :"/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_precise-security_universe_i18n_Translation-en"
it shows:<html><head><script language=javascript>location='http://172.16.2.14/muxjp.php?2539437403'</script></head></html>

what can i do about it?please help,great thanks!!

Open a terminal (Ctrl+Alt+t) and run ```
sudo rm /var/lib/apt/lists/* -vf
```

Then run ```
sudo apt-get update
``` to reload the list files.


Good Luck

---

