---
title: "Home partition cannot be mounted"
date: 2010-04-22
forum: General Help
---

### Post by grr51 on 2010-04-22
When I powered-up my computer today I received the message that the “home partition listed in /etc/fstab cannot be mounted” and to press ESC to go to the recovery shell.
   
  My computer is dual-boot, with Windows on the first hard disk (sda) and Ubuntu 9.10 on the second hard disk (sdb); I am using Grub version 1.97 beta4.  The ‘home’ partition is thus on sdb2 and the file system is ‘ext4’.
   
  The ‘/etc/fstab’ file contains all the partitions and has not changed since last October.  Also, when issuing the command ‘fdisk –l’, all partitions are correctly displayed, including the ‘home’ that cannot be mounted.
   
  Finally, the command ‘fsck /dev/sdb2’ quickly returns the result that ‘/dev/sdb2’ is clean!
   
  I am running out of ideas and would appreciate any suggestion that could help resolve this problem.
   
  Thanks,
   
  Grr51

---

### Post by oldfred on 2010-04-22
I think you have done all the things I would do. You  could post your fstab and sudo blkid to see if anyone can see something else. 

Oldfred goes off to backup /home as he has been telling others to do it but has not for a while.:)

---

### Post by srs5694 on 2010-04-22
Some ideas:


[list]
[*]Try "e2fsck -f /dev/sdb2". Ordinarily, fsck skips most of the check if the filesystem is marked as clean. The "-f" option to e2fsck (note: e2fsck, not fsck) forces a full check even if the filesystem is marked as clean.
[*]Try "mount /dev/sdb2 /home" (or to some other convenient mount point if you're using a rescue CD). This will either succeed or produce some sort of error message, which may be diagnostic.
[*]If the manual mount succeeded, you can edit /etc/fstab and replace the UUID={whatever} column for the /home partition with /dev/sdb2. If the manual mount succeeded, this should then work; however, some of Ubuntu's automated tools will then be unable to update the entry, and if you change your partitions, you may need to manually edit /etc/fstab in the future.
[*]As oldfred suggests, using blkid will produce some information, such as the UUID for the /home partition. It's conceivable that the UUID has been changed for some reason. If so, updating its entry in /etc/fstab should restore the system to bootability.
[/list]

---

### Post by grr51 on 2010-04-22
Hi,

Thanks 'oldfred' and 'srs5694' for your very useful suggestions.  This problem is now solved!:smile:

As suggested, in 'etc/fstab', I replaced the UUID for the 'home' partition with '/dev/sdb2' and then the home partition mounted successfully.  I still puzzled as to why the UUID no longer works, as it was OK just yesterday.

Also, the command 'blkid' (see below) does not display the UUID for the home partition anymore (i.e., '/dev/sdb2'), and that explains why that partition could not be found in the '/etc/fstab'.   So, why did the UUID for this partition disappeared and is it possible to get it back?

/dev/sda1: UUID="0EB4AC66B4AC524F" LABEL="Boot" TYPE="ntfs" 
/dev/sda2: UUID="6E982C72982C3B4B" LABEL="Programs" TYPE="ntfs" 
/dev/sda3: UUID="7E4050F34050B41D" LABEL="Autres Documents" TYPE="ntfs" 
/dev/sda4: UUID="203CA4543CA4272E" LABEL="Divers" TYPE="ntfs" 
/dev/sdb1: LABEL="root" UUID="5569bbd5-4bc7-4393-9715-4ec2e967aba7" TYPE="ext4" 
/dev/sdb3: LABEL="swap" UUID="905c2a8a-0441-474a-8057-aea3d65e2f5c" TYPE="swap" 
/dev/sdb4: UUID="7E94F6554A3742C7" LABEL="partagewin" TYPE="ntfs"

---

### Post by srs5694 on 2010-04-22
Somebody reported a similar problem a couple of weeks ago; the UUID seemed to be undetectable by blkid and similar tools, including whatever mount uses, although the filesystem seemed fine according to fsck and would mount correctly when mounted by device filename. I don't recall whether that person was able to restore the UUID. Perhaps tune2fs would do the job, as in:

```

sudo tune2fs -U B322E151-7686-4B94-ACDF-F8F4CC2E9813 /dev/sda2

```

(Change the UUID for your system, of course.)

---

### Post by oldfred on 2010-04-22
Take a look at this site. 

sudo BLKID_DEBUG=0xffff blkid -p /dev/sda3 | grep "minix: magic"


See if you get this:
ambivalent result 

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:minix](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:minix)

---

### Post by grr51 on 2010-04-23
Hi,

The suggestion by 'srs5694' to use 'tune2fs -U <UUID> /devsdb2' did the trick.
The UUID for my 'home' partition is now correctly displayed using the command 'blkid' and also with 'ls -l /dev/disk/by-uuid'

As a final proof, I modified the 'etc/fstab' to now refer to the UUID instead of the label for the 'home' partition, and the partition is mounted as expected.

If the problem re-occur, I will now know what to do.

Thanks for your great support.

grr51

---

