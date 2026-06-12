---
title: "Error report."
date: 2009-08-25
forum: General Help
---

### Post by Elysian° on 2009-08-25
Hello all, so, I started using Ubuntu a few weeks ago, and, today I got this error report, at first I thought it was because I was having issues with my internets, but as it turns out the error report pops up everytime I try running Synaptic, Add/Remove, update manager and while trying to uninstall wine usgin "sudo apt-get remove wine", so I figured it was something major and here I am. The error is as follows for Add/Remove first, then Synaptic, update manager and from my attempt to uninstall wine via the terminal:

 Add/Remove

This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'.

Synaptic

E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/hr.archive.ubuntu.com_ubuntu_dists_jaunty-updates_restricted_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.

Update Manager

Could not initialize the package information

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/hr.archive.ubuntu.com_ubuntu_dists_jaunty-updates_restricted_binary-i386_Packages, E:The package lists or status file could not be parsed or opened.'

Terminal

elysian@elysian-desktop:~$ sudo apt-get remove wine
[sudo] password for elysian: 
Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/hr.archive.ubuntu.com_ubuntu_dists_jaunty-updates_restricted_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.
elysian@elysian-desktop:~$ 

-------------------------------------------------------------------------------------------------------

So, I think that would be all the info I have, from what I gather that thar  "/var/lib/apt/lists/hr.archive.ubuntu.com_ubuntu_dists_jaunty-updates_restricted_binary-i386_Packages" is doing or not doing something that it shouldn't be doing or not doing. So yea, as I said I'm pretty new to Ubuntu so bare with me.

---

### Post by Elysian° on 2009-08-26
Self-bump because it's still borked and I have nowhere else to turn to?

---

