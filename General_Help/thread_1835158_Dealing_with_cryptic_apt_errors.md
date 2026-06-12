---
title: "Dealing with cryptic apt errors"
date: 2011-08-28
forum: General Help
---

### Post by freakalad on 2011-08-28
I'm not new to Ubuntu (been around from the earliest days), but this has always been something that I assumed was me doing something wrong, but I've come to the conclusion that this is a fundamental flaw in the design logic - cryptic error messages to pretty run-of-the-mill actions.

My particular beef relates to apt - periodically I may be installing or upgrading software from the repo's, & then the setup would fail completing due to some, frankly, B/S reason!
It's fine if an install fails for a legitimate reason, such as an unmet dependency, but then I would at the very least expect some meaningful error message, so that I  an at least try & address the root cause, fix it & then carry on!

The latest one I'm dealing with, is when upgrading a very vanilla instance of a Zentyal (old eBox) system, nothing weird, but at upgrade I'm presented with an "error code (1)" - what the heck an I supposed to do with "error code (1)"? 
Googling & searching on the forum indicates that this is not something new,pretty widespread & that there is no consistent & simple (to laymen users) way to of dealing with the issue.

```

$ sudo apt-get -y dist-upgrade 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up $SOME_PACKAGE ($VERSION) ...
dpkg: error processing $SOME_PACKAGE (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 grub-pc
E: Sub-process /usr/bin/dpkg returned an error code (1)

``` 

I've tried (no dice!):
```

$ sudo dpkg --configure -a
Setting up $SOME_PACKAGE ($VERSION) ...
dpkg: error processing $SOME_PACKAGE (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 $SOME_PACKAGE

```

and event tried removing, purging & reinstalling, but still the same non-result.
(and through all this the multitude of logs is not much help)

This is not the first time I've encountered this, on this or any other system or package.

Can someone please point me in the direction of a guide on dealing with the issue & ways of making meaningful sense of the situation?

---

