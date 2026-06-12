---
title: "dpkg: error:!"
date: 2012-04-22
forum: General Help
---

### Post by davesbrain on 2012-04-22
Well, this sucks.  After trying to reinstall mplayer after a 'partial upgrade' mishap...I now get this error when trying to install or remove 'anything'.  I wonder what else got hosed?!
Anyways, here's what it's telling me:
```
dpkg: error: parsing file '/var/lib/dpkg/status' near line 23608 package 'compiz-switch':
 junk after word in 'priority' feild
E: Sub-process /usr/bin/dpkg returned an error code (2)
A package failed to install.  Trying to recover:
dpkg: error: parsing file '/var/lib/dpkg/status' near line 23608 package 'compiz-switch':
 junk after word in 'priority' feild 
```


Ubuntu 10.04LTS

*Update - I replaced the word 'Low' with 'Optional' at line 23608 in the /var/lib/dpkg/status.  Ran Synaptic again and did not get any error messages at all regarding dpkg.  I then re-installed Mplayer and un-installed compiz-switch(never used it anyways).

---

