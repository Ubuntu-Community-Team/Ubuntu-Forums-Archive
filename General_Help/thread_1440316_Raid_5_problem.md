---
title: "Raid 5 problem"
date: 2010-03-27
forum: General Help
---

### Post by spiffyville on 2010-03-27
Greetings all! I'm new to ubuntu but am liking what I've seen so far. 

Anyway heres my issue. I've created a Raid 5 array using 5 1tb drives. Formatted with ext4. The array mounts and works correctly. As soon as I reboot the system though the array comes up as partially assembled with one disk showing up as spare. I can stop the array then restart it and it comes up correctly and I'm able to mount the file system again. I'm trying to figure out where I went wrong here. Any help is greatly appreciated. 

Thanks!

---

### Post by spiffyville on 2010-03-27
This is my mdadm.conf file. If any other files would be useful please let me know.

# mdadm.conf
#
# Please refer to mdadm.conf(5) for information about this file.
#

# by default, scan all partitions (/proc/partitions) for MD superblocks.
# alternatively, specify devices to scan, using wildcards if desired.
DEVICE partitions

# auto-create devices with Debian standard permissions
CREATE owner=root group=disk mode=0660 auto=yes

# automatically tag new arrays as belonging to the local system
HOMEHOST <system>

# instruct the monitoring daemon where to send mail alerts
MAILADDR root

# definitions of existing MD arrays
ARRAY /dev/md/Everything level=raid5 metadata=1.2 num-devices=5 UUID=911fb64b:a0ce9b83:050a9228:c0db3ecd name=:DATA

# This file was auto-generated on Wed, 24 Mar 2010 21:17:53 -0500
# by mkconf $Id$

---

