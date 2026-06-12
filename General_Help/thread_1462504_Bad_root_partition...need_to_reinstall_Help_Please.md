---
title: "Bad root partition...need to reinstall Help Please!"
date: 2010-04-25
forum: General Help
---

### Post by jtbse on 2010-04-25
Somewhat of a newbie here, and I'm in a fix.  After much searching, I'm having trouble finding a solution to exactly what I need to do.

Running Ubuntu Server 9.10 and have the following disks on the system

/dev/sdc1 - SCSI 18 GB, root, swap and tempfs
/dev/sdd1 - SCSI 18 GB /home not bootable

/dev/media_vg/media_lv - striped volume group of 2 SATA drives mounted as /data

My boot drive (/dev/sdc1) had gone south.  When going into rescue mode from my live cd, sometimes I can see it and sometimes I can't...basically a hardware problem.

So what I want to do is remove /dev/sdc1 from the system and do a fresh install of my ubuntu system on  the disk currently known as /dev/sdd1.  I don't really care about preserving settings, contents of /home or installed packages at this point.  But I *do* care about the contents of the striped logical volume mounted on /data

How can I install fresh without losing my logical volume?

Thanks

---

### Post by jtbse on 2010-04-25
Ok..

I guess I was just making this more difficult that I needed to.

I followed the instructions here:

[http://tldp.org/HOWTO/LVM-HOWTO/recipemovevgtonewsys.html](http://tldp.org/HOWTO/LVM-HOWTO/recipemovevgtonewsys.html)

After managing to boot from live cd, I ran "vgchange" and "vgexport" on the volume group.

Then I shutdown the system, disconnected the problematic disk as well as the SATA drives that make up the volume group (didn't want to run any risk of overwriting them) and re-ran the Ubuntu server install of the base system on the working SCSI disk (now /dev/sda1).

After the base install, I installed lvm2 and shutdown the system.

Then I reattached the two SATA drives and rebooted.

Running "pvscan", "vgimport", and "vgchange" made my old volume group available again.

So all I had to do at that point was mount it and everything was there!

---

