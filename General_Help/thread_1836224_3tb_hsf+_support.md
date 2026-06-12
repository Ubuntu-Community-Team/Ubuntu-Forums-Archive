---
title: "3tb hsf+ support"
date: 2011-08-30
forum: General Help
---

### Post by nebuk89 on 2011-08-30
Hi all
I am quite new to ubuntu and I am trying to get my hfs+ 3tb hdd to work under ubuntu, I know support was removed in Feb due to corruption and damage to drives but I can't seem to find any word of change. Could anyone point me in the right direction? 
Many thanks
Ben

---

### Post by mike555 on 2011-08-30
If you are trying to read the hsf+ drive from ubuntu you probably need to install "  hfsplus " from your package manager ...

---

### Post by nebuk89 on 2011-08-31
Hi
I have HFSplus the issue is that when mounting a drive over the size of 2tb you get
Error mounting: mount: wrong fs type, bad option, bad superblock on /dev/sde2,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

as currently there is a issue with this, I was wondering if anyone had a temporary patch which worked around this at all
My 2tb and 1tb HFSplus drives are working fine it is just the 3tb that is the issue, for example
[http://www.spinics.net/lists/linux-fsdevel/msg42242.html](http://www.spinics.net/lists/linux-fsdevel/msg42242.html)
But I am still a bit new to ubuntu to know how to apply a change like this to the system, any help would be appreciated

---

