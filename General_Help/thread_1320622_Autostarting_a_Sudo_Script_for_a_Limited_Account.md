---
title: "Autostarting a Sudo Script for a Limited Account?"
date: 2009-11-09
forum: General Help
---

### Post by MasterNetra on 2009-11-09
With that Kernel hole I was hoping to produce a autostart script to change the mmap_min_addr to something other then zero. However to do this it seems it requires the use of Sudo...or such privileges. Anyone know how I can do this Universally? Like if Ubuntu has a master auto-script folder somewhere in its system files?

---

### Post by phrostbyte on 2009-11-09
Take a look at:

/etc/init.d/ 

:D

---

### Post by phrostbyte on 2009-11-09
Actually mmap_min_addr is set to something other then 0 in Ubuntu by default. When you install Wine the installer sets it to 0. Perhaps uninstalling Wine is an easier solution then writing an init job. :)

---

### Post by MasterNetra on 2009-11-09
> **phrostbyte said:**
> Actually mmap_min_addr is set to something other then 0 in Ubuntu by default. When you install Wine the installer sets it to 0. Perhaps uninstalling Wine is an easier solution then writing an init job. :)

Not really considering I require the use of wine for some must have windows apps atm.

Though I'm having some issues writing the the script.

Script name: securemmap.sh
Permissions: 755
Allow file executing as program: Yes (checked)
Owner: root
Group: root
Content:
```

sysctl -w vm.mmap_min_addr="7500"

exit

```

***"Number changed to protect actual"***

Doesn't work. Any thoughts? I have little to no experiance in righting scripts but would like to get this to work.

---

### Post by sisco311 on 2009-11-09
Create a new conf file in /etc/sysctl.d (see /etc/sysctl.d/README):
```
gksu gedit /etc/sysctl.d/60-vm.mmap_min_addr.conf
```

add this line to the file:
```

vm.mmap_min_addr = 7500
```
save it and exit.

run:
```
 sudo service procps restart
```
or reboot.

---

### Post by MasterNetra on 2009-11-09
Actually I got it to work.

Contents:
```

#!/bin/sh

sysctl -w vm.mmap_min_addr="65536"

exit 1

```

And apparently I had forgotten to do

```

sudo update-rc.d securemmap.sh defaults

```

Afterwards it works! Yay!
Thanks everyone for your help or attempts at helping. ^.^

---

