---
title: "Some apps will not start"
date: 2011-10-03
forum: General Help
---

### Post by vlamnire on 2011-10-03
So far I have tried to open Zim Desktop Wiki and the Ubuntu Update Manager and neither will start.  I looked at dmesg I have the log here (scroll to bottom for update manager and zim): [http://dl.dropbox.com/u/6575036/dmesg.txt](http://dl.dropbox.com/u/6575036/dmesg.txt)



```
[   98.791731] update-manager[2068]: segfault at 27 ip 00368392 sp bf8b8ee0 error 4 in libgdk-x11-2.0.so.0.2200.0[32c000+94000]
[  133.289885] update-manager[2140]: segfault at 7 ip 006d0392 sp bf8f04b0 error 4 in libgdk-x11-2.0.so.0.2200.0[694000+94000]
[  184.380807] ath9k: DMA failed to stop in 10 ms AR_CR=0x00000024 AR_DIAG_SW=0x00000020
[  262.256606] zim[2214] general protection ip:3d4226 sp:bfd1bb50 error:0 in libglib-2.0.so.0.2600.1[378000+cd000]
```How can I correct this?  I'd figure a reinstallation of those packages (libgdk and libglib) would work but I want to make sure.  I also cannot use add-apt-repository command either that comes up with:
```
Traceback (most recent call last):
  File "/usr/bin/add-apt-repository", line 55, in <module>
    sp = SoftwareProperties()    
  File "/usr/lib/python2.6/dist-packages/softwareproperties/SoftwareProperties.py", line 90, in __init__
    self.reload_sourceslist()
  File "/usr/lib/python2.6/dist-packages/softwareproperties/SoftwareProperties.py", line 538, in reload_sourceslist
    self.distro.get_sources(self.sourceslist)    
  File "/usr/lib/python2.6/dist-packages/aptsources/distro.py", line 90, in get_sources
    raise NoDistroTemplateException("Error: could not find a "
aptsources.distro.NoDistroTemplateException: Error: could not find a distribution template
```

---

