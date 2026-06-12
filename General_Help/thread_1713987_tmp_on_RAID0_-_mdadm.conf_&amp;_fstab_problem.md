---
title: "/tmp on RAID0 - mdadm.conf &amp; fstab problem"
date: 2011-03-24
forum: General Help
---

### Post by broos on 2011-03-24
My system is 64 bit 10.04 on an HP xw8600.  It took a while but with some forum searching and trial and error I figured out how to create a 2 disk RAID0 that assembles and starts at boot-up.  However, if I try to have /tmp mount on this volume by adding a line for it to fstab it causes an error.    The error is averted if I comment out the md0 line in fstab.  The error returns if I uncomment that line. 

The error: 
**[COLOR=DarkRed]There is a problem with the configuration server. [/COLOR]**
- (/usr/lib/libgconf2-4/gconf-sanity-check-2 exited with status 256)

Another error to do with configuration defaults for the Gnome power manager appears in a box in the upper right hand corner of the screen.

I googled the error message and one of the reported fixes was to manually set the permissions for /tmp to 0777.  That tip about setting /tmp permissions to 0777 looked like a good lead since when I took a more critical look at my mdadm.conf file I found that the default CREATE line sets "debian default permissions" on the RAID volume, permissions of 0660.   That would not be correct for /tmp.  So, I did two things:   1).  chmod 0777 /dev/md0, and 2).  Changed permissions on the line in mdadm.conf I mentioned above to 0777.  I still can not uncomment the md0 line in fstab without causing the error again.

I have run out of ideas now.  Do any of you know how to go about this?

Thanks,
broos

P.S. Since I'm sure someone will ask I pasted the line from fstab and the mdadm.conf file below.

This is the md0 line in fstab:

```
# md0 is a striped RAID to be mounted as /tmp
#/dev/md0             /tmp          auto      defaults      0       0


```and this is the mdadm.conf file contents:

```
# mdadm.conf
#
# Please refer to mdadm.conf(5) for information about this file.
#

# by default, scan all partitions (/proc/partitions) for MD superblocks.
# alternatively, specify devices to scan, using wildcards if desired.
DEVICE partitions

# auto-create devices with Debian standard permissions for /tmp
CREATE owner=root group=disk mode=0777 auto=yes

# automatically tag new arrays as belonging to the local system
HOMEHOST <system>

# instruct the monitoring daemon where to send mail alerts
MAILADDR root

# definitions of existing MD arrays
#ARRAY /dev/md0 level=raid0 num-devices=2 UUID=c80d65ba:961f13d5:6c2f1fc7:5a13eefb

# This file was auto-generated on Wed, 16 Mar 2011 11:03:12 -0700
# by mkconf $Id$
ARRAY /dev/md0 level=raid0 num-devices=2 metadata=00.90 UUID=584fda2e:6f46a65c:6c2f1fc7:5a13eefb
```

---

