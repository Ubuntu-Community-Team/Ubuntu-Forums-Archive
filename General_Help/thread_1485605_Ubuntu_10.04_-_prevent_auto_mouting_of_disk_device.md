---
title: "Ubuntu 10.04 - prevent auto mouting of disk devices"
date: 2010-05-17
forum: General Help
---

### Post by abjork on 2010-05-17
In 8.04 it was easy to adjust, but with 10.04 I've tried to set the policies for udisks with no luck.

I want Ubuntu to always ask for my password when a new device/disk is added to the system. If I don't give my password it should not mount the device. What happens now is that all disks added is mounted without any question leading me to believe that the policies is ignored (by a bug) or that I've missed something. I've been through obvious setting in the graphical shell and disabled them. But if they'd been enabled the policies should have kicked in.

I do think it worked in version 9.10 when I tested it earlier this year or late last year, but I was waiting for the next LTS.


[LIST]
[*]How may I set up Ubuntu 10.04 to make it work as intended?
[/LIST]

---

### Post by foresthill on 2010-05-17
I asked the same question a while back, and in this thread you will find the solution (as well as reasons why it's unnecessary, which I strongly disagree with):

[http://ubuntuforums.org/showthread.php?t=1477756](http://ubuntuforums.org/showthread.php?t=1477756)

---

### Post by bodhi.zazen on 2010-05-17
Moved to general help as I think you will get an answer in GH faster then Security.

As to if this is a security problem or not is debatable, could go either way, depending on your environment.

I would only point out that, IMO, physical access == root access and mounting drives or partitions is, IMO, missing the huge problems caused physical access.

---

### Post by abjork on 2010-05-17
> **bodhi.zazen said:**
> ...
As to if this is a security problem or not is debatable, could go either way, depending on your environment.

I would only point out that, IMO, physical access == root access and mounting drives or partitions is, IMO, missing the huge problems caused physical access.

I'm testing Ubuntu from a forensic point of view. It's vital that no disks other than the ones listed in fstab gets mounted without some form for authentification from the user. This means no disks attached by USB, FireWire, eSata, scsi or motherboard sata-ports should mount automatically unless they are in fstab.

---

### Post by fix_ on 2010-05-18
Following sequence can be useful (at least for usb):

1. Allow root only access to /media, where all stuff is mounted
```

chmod -R 700 /media

```
2. create /etc/init.d/stop_udev.sh:
```

#!/bin/bash
udevadm control --stop-exec-queue

```
3. allow it to be executed
```

chmod +x /etc/init.d/stop_udev.sh

```
4. register on all runlevels
```

update-rc.d stop_udev.sh

```
5. edit /etc/grub.d/:
```

change &#8220;ro $2&#8221; to &#8220;ro nousb $2&#8221;

```
6. update grub
```

update-grub

```

All these reciped are useless if your malicious person has physical access to PC and data is not encrypted. So, start with encrypting hard-drive (easiest way - clean install from alternate CD and choosing option to set up encrypted LVM).

---

### Post by dcstar on 2010-05-18
> **abjork said:**
> I'm testing Ubuntu from a forensic point of view. It's vital that no disks other than the ones listed in fstab gets mounted without some form for authentification from the user. This means no disks attached by USB, FireWire, eSata, scsi or motherboard sata-ports should mount automatically unless they are in fstab.

Simply set up the user account without those privileges.

I just did that and mounting any previously unmounted partition prompts for the admin account password.

Edit - that only worked for internal drives, the external ones still mounted without prompting.

---

