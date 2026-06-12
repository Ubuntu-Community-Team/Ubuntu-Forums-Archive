---
title: "Major Update Manager Error (not 11.10 related)"
date: 2011-10-14
forum: General Help
---

### Post by dvaldes21 on 2011-10-14
Hey guys,
So I'm trying to run the update manager and get the following error: 
> 
Could not initialize the package information

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E: Problem parsing dependency Suggests, E:Error occurred while processing libsane (NewVersion2), E: Problem with MergeList /var/lib/dpkg/status, E:The package lists or status file could not be parsed or opened.'I've scoured the internet for this, and have been able to find nothing. Any ideas??

Also, running the Synaptic Package Manager gives me this error:
> E: Problem parsing dependency Suggests
E: Error occurred while processing libsane (NewVersion2)
E: Problem with MergeList /var/lib/dpkg/status
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.Since this error began, a bunch of other weird stuff has been happening. Software is crashing randomly, the icons on my Unity dashboard always return to default after rebooting, and sometime even the entire system crashes.

I am still using 11.04. Any help would really appreciated.

---

### Post by Rubi1200 on 2011-10-15
Try running the following commands in the terminal:
```
sudo rm /var/lib/apt/lists/* -vf
sudo apt-get update
```

The first command removes corrupted package lists, the second one refreshes them.

---

