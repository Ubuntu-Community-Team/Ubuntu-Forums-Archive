---
title: "Add/Remove programs problem - please HELP"
date: 2010-06-08
forum: General Help
---

### Post by bobmac on 2010-06-08
Folks,

When I open the Add/Remove option from the Applications menu I get this message.

Failed to check for installed and available applications

This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'.

When I do the apt-get stuff it would appear that the system is trying to get rid of something called phpadmin. I've no idea what this is and it seems that the system can't get rid of it.

Can anyone help

Regards,

Bob

---

### Post by mikewhatever on 2010-06-08
Please post the output
```
sudo apt-get update && sudo apt-get install -f
```

---

### Post by bobmac on 2010-06-09
The sudo apt-get update && sudo apt-get install -fsudo apt-get update && sudo apt-get install -f command didn't work. A message appears:

The following packages will be REMOVED:
  phpmyadmin
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 10.4MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 115908 files and directories currently installed.)
Removing phpmyadmin ...
dpkg: error processing phpmyadmin (--remove):
 subprocess post-removal script returned error exit status 10
Errors were encountered while processing:
 phpmyadmin
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

