---
title: "urgent: need help cloning partition to ext. hdd to use in same computer"
date: 2009-08-16
forum: General Help
---

### Post by uschxc on 2009-08-16
Hey guys and gals,

I blame myself, but I'm under the gun on this one.  I have a linux system with a 500 gig hard drive where /dev/sda1, the complete system (/boot, /home, everything else), is partitioned at 107 gigs with 52 gigs free.

I have an external hard drive, which we'll call /dev/sdb) that is 140 gigs and I need to clone /dev/sda1 to it so I can have the same environment on an alternate hard drive that will be used in the same computer.

From what I know, I can boot from a live cd and run
```
dd if=/dev/sda1 of=/dev/sdb
```
and it will copy the sda1 partition to the drive sdb.  However I am not aware if this will also make sdb bootable and i'm ultimately looking for a turn key operation.

Could someone post/link a quick tutorial on how to take /dev/sda1 and clone it to /dev/sdb and after the dd command /dev/sdb should be bootable and good to go?  

The big issue is I only have time for one shot at the dd command since it will take hours and I need to make sure its all setup and prep'd to function properly.  I would do all the googling and searching myself but I'm going to be on an airplane for the next 16 hours.

PLEASE help me community..

V/r
Adam Turner

---

### Post by lessgov2007 on 2009-08-16
I don't know, but I'd like too.

---

### Post by quixote on 2009-08-16
I haven't used dd for this myself.  I've used [clonezilla]("http://clonezilla.org"), but, as far as I know, yes, if you make a direct to disk copy by whatever method, if it's *nix-based, it'll be bootable.  I don't vouch for windows.  In that case, probably not.  If the external drive will be USB-connected, there can be boot issues because some drives take long enough to come up that the boot process loses interest.  There are fixes for that, such as supergrub.

I realize you're pressed for time, but I'd suggest trying a dry run where you exclude all the data directories.  I don't know how you'd do that with dd (maybe somebody else here does ?), but I know you can do it with Clonezilla.  It would take an hour or so to 1) download C-zilla, 2) burn the CD 3) boot your computer with the CD 4) select the directories and destination drive 5) wait about 15 minutes for the transfer (clonezilla is fast) and 6) see if the new drive boots.

Worth  the extra time, perhaps.

---

### Post by MrUmunhum on 2009-08-16
> **uschxc said:**
> Hey guys and gals,

I blame myself, but I'm under the gun on this one.  I have a linux system with a 500 gig hard drive where /dev/sda1, the complete system (/boot, /home, everything else), is partitioned at 107 gigs with 52 gigs free.

I have an external hard drive, which we'll call /dev/sdb) that is 140 gigs and I need to clone /dev/sda1 to it so I can have the same environment on an alternate hard drive that will be used in the same computer.

From what I know, I can boot from a live cd and run
```
dd if=/dev/sda1 of=/dev/sdb
```
and it will copy the sda1 partition to the drive sdb.  However I am not aware if this will also make sdb bootable and i'm ultimately looking for a turn key operation.

Could someone post/link a quick tutorial on how to take /dev/sda1 and clone it to /dev/sdb and after the dd command /dev/sdb should be bootable and good to go?  

The big issue is I only have time for one shot at the dd command since it will take hours and I need to make sure its all setup and prep'd to function properly.  I would do all the googling and searching myself but I'm going to be on an airplane for the next 16 hours.

PLEASE help me community..

V/r
Adam Turner

Adam,
  You left out some important information:[LIST=1]
[*]Are you currently using a boot loader, which one?
[*]Does you BIOS support USB boots? I am assuming the external drive is USB.
[*]Are you using the BIOS boot manager?
[/LIST]
Also you may need to update /etc/fstab if yes to #3. If you are using your BIOS boot manager then he will reconfigure the way order of the drives. If any case. I recommend using the 'LABEL=' option of the kernel.

I don't remember but you may need to fix the target partition after the DD operation. It may not reflect the correct partition size??

The simple answer is yes, it should work. Do the DD and then see if it boots. 

Your DD example is wrong. SHould be 'dd if=/dev/sda of=/dev/sdb' I think?
Or maybe 'dd if=/dev/sda1 of=/dev/sdb1', you will need to fdisk the target drive.

---

### Post by XPuntu on 2009-08-16
Read this:

[http://www.arsgeek.com/2008/01/22/how-to-clone-your-bootable-ubuntu-install-to-another-drive/]("http://www.arsgeek.com/2008/01/22/how-to-clone-your-bootable-ubuntu-install-to-another-drive/")

You need to re-install grub after cloning but it's not too hard.

---

