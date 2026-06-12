---
title: "LVM recovery"
date: 2011-07-30
forum: General Help
---

### Post by Perkins on 2011-07-30
I have a system set up with an an encrypted partition.  Inside the encryption is an LVM group.  Inside the LVM group is my root filesystem.  It worked rather nicely until the LVM decided to randomly start giving a "Incorrect metadata area header checksum" error.  Unfortunately, the recovery process from such errors that I have found requires pulling a file from /etc/lvm2, which I can't get to.  I've tried GPart, which can tell me that my filesystem is still there, but it doesn't know how to generate the LVM metadata about where and what it is.  Is there a similar tool to recover the partition information for LVM?  Or are there newer methods to use?  (Most of the posts I've found date from '06.)

---

### Post by bodhi.zazen on 2011-07-30
Well, by far the easiest solution is going to be to restore from backup.

Recovery is going to be more difficult due to the encryption.

Boot a live CD, decrypt the crypt, then attempt to recover the LVM

I assume you understand how to decrypt the LUKS crypt ;) If not see

[http://ubuntuforums.org/showthread.php?p=4530641](http://ubuntuforums.org/showthread.php?p=4530641)

OK, now try to recover your LVM

[http://tldp.org/HOWTO/LVM-HOWTO/recovermetadata.html](http://tldp.org/HOWTO/LVM-HOWTO/recovermetadata.html)

[http://blog.adamsbros.org/2009/05/30/recover-lvm-volume-groups-and-logical-volumes-without-backups/](http://blog.adamsbros.org/2009/05/30/recover-lvm-volume-groups-and-logical-volumes-without-backups/)

Post any error messages or questions.

---

### Post by Perkins on 2011-08-01
Hmmm...  Well, for a while there I thought that was going to work...  

Ok, so the first recovery link assumes you can get to a backup of your metadata.  Which I can't.  The second one should work, however, when I try to find the metadata, I get:

```

root@lmp-laptop:~# pvck -d -v /dev/mapper/udisks-luks-uuid-e389706f-3e9a-4820-b287-af982b7c6a62-uid1000 
    Scanning /dev/mapper/udisks-luks-uuid-e389706f-3e9a-4820-b287-af982b7c6a62-uid1000
  Incorrect metadata area header checksum
  Found label on /dev/mapper/udisks-luks-uuid-e389706f-3e9a-4820-b287-af982b7c6a62-uid1000, sector 1, type=LVM2 001
  Found text metadata area: offset=4096, size=192512
  Incorrect metadata area header checksum

```

When I open the device in a hex editor and go to offset 0x1000 (which should be the "text metadata area") the contents are illegible.  And, as you can see, there are no "metadata record" entries.  

Is the backup copy that's supposedly stored in /etc/lvm/archive one that will be included in what pvck can find?  Or should I take the hex editor and see if I can find that file on the disk?

---

### Post by Perkins on 2011-08-04
Alright.  To answer my own question, no, the backup copy from /etc/lvm/archive is not necessarily included in the output of pvck.  So, fire up hexedit on the device in question, hit tab once to switch to ASCII mode, and then / to search for "physical_volumes {"  

Note also that a keyword search through a 2Tb disk to find the backup copy takes about a day and a half.  So be patient.


For anyone else attempting to fix a similar problem, once you have the backup of the metadata, and have determined which one is the correct one (it keeps multiple copies)  Use 
```
pvcreate -ff -u <id> --restorefile <metadata file> <device>


```

to re-allocate the physical volume where <id> is the UUID of the physical volume in question from the config file.

Then use 
```

vgcfgrestore -f <metadata file> -v <volume group id>

```

The volume group id will be the one where the {} encapsulates the entire rest of the description.
It's usually the first line that looks like:

<volume group id> {


After that type 
```
sudo lvm vgmknodes
```

To create handles in /dev/mapper you can use to access your logical volumes.

Depending on what caused your lvm crash, you might well need to fsck the partitions before they will mount.

---

### Post by bodhi.zazen on 2011-08-04
Glad you were able to solve the problem, thank you for posting your solution.

---

### Post by Perkins on 2011-08-04
Yes...  Unfortunately, in my case, whatever happened, it wasn't just the lvm that got nuked.  Fortunately, fsck was able to fix it, but all my data is in lost+found...  Ah well, having to sort it is better than losing it entirely.

---

