---
title: "FSTAB tearing my hair out"
date: 2010-03-06
forum: General Help
---

### Post by Silas (son of Silas) on 2010-03-06
For months my 64bit Ubuntu setup has been working perfectly. This evening I installed Virtualbox, setup an windows XP guest on a LVM no problems.

After a reboot to my surprise my logical volume didn't mount. After some fiddling I have discovered that if I remove it from my fstab and reboot I can mount it manually, but if I add it back into the fstab it doesn't mount and I can no longer mount it manually, giving me an error that says it is either already mounted or that the mount point is busy.

my fstab looks like this:

> 
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0

# / was on /dev/sda1 during installation
UUID=3a778823-faf0-41a5-bb35-7f717339d6b5 /               ext4    errors=remount-ro 0       1

/dev/backup_lvg/backup_lv               /home/silas/Backup_LV              ext3    defaults        1 2
/dev/mediaserver_lvg/mediaserver_lv           /home/silas/Mediaserver_LV         ext3    defaults        1 2
if I comment out the last line, reboot and type the following from a terminal it mounts perfectly.

> sudo mount /dev/mediaserver_lvg/mediaserver_lv  /home/silas/Mediaserver_LV

What on earth is going on here?

---

### Post by flippo on 2010-03-06
I haven't used Virtualbox personally, but is the device your trying to mount actually ext3?

To check try:```
sudo mount -t ext3 /dev/mediaserver_lvg/mediaserver_lv /home/silas/Mediaserver_LV 
```

---

### Post by Silas (son of Silas) on 2010-03-06
Yep, that works perfectly. The logical Volume is ext3.

Something broke when I installed VirtualBox, or maybe it's a coincidence? I removed VirtualBox and the problem still remains.

The Logical Volume mounts perfectly when it's done manually, but when it's in the fstab it won't mount, yet that line has been working perfectly in my fstab for months.

---

### Post by flippo on 2010-03-06
sorry, was my only idea...  Sounds very odd to me.  If the fstab fails to mount it should be in a log somewhere though... (/var/log/...)

---

### Post by dcstar on 2010-03-06
> **Silas (son of Silas) said:**
> Yep, that works perfectly. The logical Volume is ext3.

Something broke when I installed VirtualBox, or maybe it's a coincidence? I removed VirtualBox and the problem still remains.

The Logical Volume mounts perfectly when it's done manually, but when it's in the fstab it won't mount, yet that line has been working perfectly in my fstab for months.

Possibly the LVM service is not starting quickly enough any more because Virtualbox changed something.

You may want to do a reinstall of all the LVM packages and reconfigure them to defaults.

---

### Post by Silas (son of Silas) on 2010-03-06
OK Fixed it.

By changing the fstab to reference the logical volume by its UUID the problem went away.

I identified the UUID of the logical volume by typing (note: I highlighted the relevant UUID in red):

> 
$ sudo blkid
/dev/sda1: LABEL="ubuntu64" UUID="3a778823-faf0-41a5-bb35-7f717339d6b5" TYPE="ext4" 
/dev/sda3: UUID="DBCT99-U0oi-FbBS-UVWc-GzSK-8ehq-hn5yXQ" TYPE="LVM2_member" 
/dev/sdb1: UUID="Kxc2N7-tfIR-rM5L-vNF9-27f3-xfp8-25v9jC" TYPE="LVM2_member" 
/dev/sdc1: UUID="hmvdWO-riTr-mqXE-fd6O-E8zT-ytwR-w0PEuv" TYPE="LVM2_member" 
/dev/mapper/backup_lvg-backup_lv: UUID="1b69c822-4ccc-4a6b-8b34-30f5ea7b81b3" TYPE="ext3" 
/dev/mapper/mediaserver_lvg-mediaserver_lv: [COLOR=red]_UUID="0a5e118d-cea5-438c-b71f-41975ce68764_[/COLOR]" TYPE="ext3" 


Then I modified the entry in my fstab that reference the logical volume thus:

> 
# Mediaserver_LV
UUID=0a5e118d-cea5-438c-b71f-41975ce68764               /home/silas/Mediaserver_LV         ext3    defaults        1 2
After a reboot all was well in Silas town :)

---

### Post by Silas (son of Silas) on 2010-03-08
Hmm.. This was all peachy yesterday but now its back. Interestingly if I reboot a few times my two logical volumes (both of which are now identified by their UUID in my fstab randomly refuse to mount. Sometimes one will mount sometimes the other.

Weird.

---

### Post by Silas (son of Silas) on 2010-03-08
Oddly, the top command reveals that fsck.ext3 is the process using the most CPU.

If I remove the troublesome LV from fstab fsck.ext3 disappears from the process list. If I add it back in, it returns. I am manually running an fsck to see what's what.

---

### Post by Silas (son of Silas) on 2010-03-08
And therein is the problem.

The disk seems to have been flagged to be checked, which meant that it was locked and couldn't be mounted. After completing a check it mounts fine, but being 3tb it takes forever.

I never connected the fact that I had been trying to get suspend to RAM working this morning that meant countless reboots which clocked up sufficient mounts on each LV to force a check.

---

