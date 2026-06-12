---
title: "Ubuntu 10.10 update manager error"
date: 2010-12-19
forum: General Help
---

### Post by Enders_Game on 2010-12-19
> Could not initialize the package information

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_maverick-security_main_binary-amd64_Packages, E:The package lists or status file could not be parsed or opened.'


I tried googling the error and all I could find was a ubuntu.ru and the problem was solved (I think) but in russian. Google translate translated it to 
"go to synaptic, select the filter "c errors", for those packages that will, to appoint "to reset, then hit apply"
Which is obviously wrong commands in english, but theres a lead...

Thanks in advance.

edit:
When I try entering synaptic from the system->admin way instead of the update icon in the tray,
I get 
> 
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_maverick-security_main_binary-amd64_Packages
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.


And the only option after that is to close (which is does), I cant really do anything in the synaptics manager.

edit2: The original "lead" was for a different error than mine so not as useful as previously thought.

---

### Post by sikander3786 on 2010-12-19
From Applications > Accessories > Terminal, post the output of this command.

```
sudo apt-get update
```

---

