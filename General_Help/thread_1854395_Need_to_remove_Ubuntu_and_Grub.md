---
title: "Need to remove Ubuntu and Grub"
date: 2011-10-04
forum: General Help
---

### Post by jbcol1 on 2011-10-04
Help!!! :confused:

I have a dell laptop running Windows 7. It has a rescue partition.

I reduced the win7 partition and created a new 25 gb part for the Ubuntu install.  When I reboot it goes to grub with my choices as Ubuntu and the Win XP boot loader.


  Both Ubuntu and Windows 7 will boot. However, around this time I started having problems with my wireless connection. Not sure if Ubuntu has any responsibility for this.
  Ultimately, I am considering restoring my laptop to factory condition. But now, I do not get that option in the boot process anymore due to Grub taking over.


  So, at this point I want to remove Grub and Ubuntu and want to restore my windows boot loader.

 
  How do I do this?
  Thanks in advance.
  John

---

### Post by Mark Phelps on 2011-10-04
If you boot into Win7, you can use the Backup feature to create and burn a Win7 Repair CD.  Then, boot from that CD and run Startup Repair at least three times.  After that, you should then be booting directly into Win7.

You can then use the Win7 Disk Management utility to remove the Ubuntu partition(s) and expand the Win7 OS partition to fill the unused space.

---

### Post by collisionystm on 2011-10-04
You also need to repair the Windows 7 MBR to remove grub. Look into that.

---

### Post by Mark Phelps on 2011-10-04
> **collisionystm said:**
> You also need to repair the Windows 7 MBR to remove grub. Look into that.

You don't need to "Look into that" -- because running Startup Repair several time WILL overwrite the current MBR with one suited to Win7.

---

### Post by fritz269 on 2011-10-04
I believe that if you remove the Ubuntu Partition and use the repair disk or the original WIN7 disk you can repair the the MBR without having to repair multiple times. It worked for me before but I have not tried it with WIN 7.

---

### Post by collisionystm on 2011-10-04
...... You can delete you ubuntu partition, fix the mbr, and re-expand your windows 7 partition all in one shot from the windows 7 setup disk. It really is not that complicated.

---

### Post by garvinrick4 on 2011-10-04
+1 for post 2

---

