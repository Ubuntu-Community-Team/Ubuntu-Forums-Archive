---
title: "Recover EXT4 Partition after GParted Kernel Panic and no viable backup Superblocks"
date: 2012-05-15
forum: General Help
---

### Post by Dead ChexMix on 2012-05-15
[B]SOLOUTION (May, 16 2012):

[/B]> **oldfred said:**
> Have you tried testdisk? It often finds old partitions.

I normally do not queue gparted operations. I want one to complete  before I even think about starting another. And I try to avoid moves if  possible as that is always to most risky. Any power failure or other  stoppage almost always leads to corruptions which may not be  recoverable.

After testdisk then photorec is the next possiblity. I have had to use photorec & it is a long tedious process.

[https://help.ubuntu.com/community/DataRecovery#Lost%20Partition](https://help.ubuntu.com/community/DataRecovery#Lost%20Partition)
repairs including testdisk info & link to testdisk, testdisk is in repository and on most repairCDs
[http://members.iinet.net.au/~herman546/p21.html]("http://members.iinet.net.au/%7Eherman546/p21.html")
[http://www.psychocats.net/ubuntucat/recoverdeletedfiles/](http://www.psychocats.net/ubuntucat/recoverdeletedfiles/)
Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)

Testdisk & photorec
[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)
[http://www.psychocats.net/ubuntucat/recoverdeletedfiles/](http://www.psychocats.net/ubuntucat/recoverdeletedfiles/)
[http://ubuntu4beginners.blogspot.com/2011/01/recover-deleted-data-using-photorec-in.html](http://ubuntu4beginners.blogspot.com/2011/01/recover-deleted-data-using-photorec-in.html)

Use scripts to help sort and rename files:
[http://www.cgsecurity.org/wiki/After_Using_PhotoRec](http://www.cgsecurity.org/wiki/After_Using_PhotoRec)
use flac tags to rename files 
[http://lglinux.blogspot.com/2008/10/use-flac-tags-to-rename-files.html](http://lglinux.blogspot.com/2008/10/use-flac-tags-to-rename-files.html)
[http://system-tricks.com/index.php/datarecovery/sort-testdisk-photorec-data-recovery-results/](http://system-tricks.com/index.php/datarecovery/sort-testdisk-photorec-data-recovery-results/)
Best GUI Indexing/Search Tool for Local Files? 
[http://ubuntuforums.org/showthread.php?t=1739701](http://ubuntuforums.org/showthread.php?t=1739701)

-oldfred


**Just used test disk to find partition and copied all files to external HDD**






Let's Start with what all My Computer is...

It's a Toshiba Laptop with a 250GB HDD (sda)

The OSes I have installed: 
Windows 7 64-bit Boot Partition (sda1)    (1.6 GB)
Windows 7 64-bit    (sda2)   (120GB)

EXTENDED PARTITION (sda4)
    Ubuntu Linux 64-bit Natty Narwhal (sda6) (70GB) [U][B]NEEDS RECOVERED
[/B][/U]    Allocated Space (10GB)
    Windows 8 64-bit Consumer Preview (sda7) (34GB)
    Swap Space (sda5) (4.2GB)
END EXTENDED PARTITION

HDDRECOVERY (sda3) (9.6GB)
    

During the Kernel Panic GParted was working on...
1. Shrinking sda2 Windows 7 (Completed I think)
2. Expanding sda4 Extended (Completed I think)
3. Shrink sda6 (FAILED)                    
4. Moving sda6 to the left (FAILED)
5. Expanding sda7 (FAILED)

The Panic occurred sometime in the midst of 3 and 4

Unfortunately, upon reboot, Grub Rescue Came up
After Booting my LiveUSB the partition comes up as just a "Linux 0x83" partition with an "unknown" file system   according to Disk Utility

I Figured just a bad super block, so I ran:
[U][I]
sudo mke2fs -n /dev/sda6[/I][/U]

to see where the Backup Super Blocks are stored...

after running:

_*sudo e2fsck -y -b ###### /dev/sda6*_
and
_*sudo e2fsck -b ###### /dev/sda6*_

With each of the backup numbers i get
"
e2fsck 1.41.14 (22-Dec-2010)
e2fsck: Invalid argument while trying to open /dev/sda6

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>
"

Any Help? I Have no Back-Up of this drive... And I need the Data off of it.
All recovery Operations are being ran from a LiveUSB Natty Narwhal 64-bit




Thanks!

---

### Post by oldfred on 2012-05-15
Have you tried testdisk? It often finds old partitions.

I normally do not queue gparted operations. I want one to complete before I even think about starting another. And I try to avoid moves if possible as that is always to most risky. Any power failure or other stoppage almost always leads to corruptions which may not be recoverable.

After testdisk then photorec is the next possiblity. I have had to use photorec & it is a long tedious process.

[https://help.ubuntu.com/community/DataRecovery#Lost%20Partition](https://help.ubuntu.com/community/DataRecovery#Lost%20Partition)
repairs including testdisk info & link to testdisk, testdisk is in repository and on most repairCDs
[http://members.iinet.net.au/~herman546/p21.html](http://members.iinet.net.au/~herman546/p21.html)
[http://www.psychocats.net/ubuntucat/recoverdeletedfiles/](http://www.psychocats.net/ubuntucat/recoverdeletedfiles/)
Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)

Testdisk & photorec
[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)
[http://www.psychocats.net/ubuntucat/recoverdeletedfiles/](http://www.psychocats.net/ubuntucat/recoverdeletedfiles/)
[http://ubuntu4beginners.blogspot.com/2011/01/recover-deleted-data-using-photorec-in.html](http://ubuntu4beginners.blogspot.com/2011/01/recover-deleted-data-using-photorec-in.html)

Use scripts to help sort and rename files:
[http://www.cgsecurity.org/wiki/After_Using_PhotoRec](http://www.cgsecurity.org/wiki/After_Using_PhotoRec)
use flac tags to rename files 
[http://lglinux.blogspot.com/2008/10/use-flac-tags-to-rename-files.html](http://lglinux.blogspot.com/2008/10/use-flac-tags-to-rename-files.html)
[http://system-tricks.com/index.php/datarecovery/sort-testdisk-photorec-data-recovery-results/](http://system-tricks.com/index.php/datarecovery/sort-testdisk-photorec-data-recovery-results/)
Best GUI Indexing/Search Tool for Local Files? 
[http://ubuntuforums.org/showthread.php?t=1739701](http://ubuntuforums.org/showthread.php?t=1739701)

---

### Post by Dead ChexMix on 2012-05-16
Thank you oldfred! You saved my Data!

I had tried  to use testdisk but failed with it the first time, tried a guide you gave and well, I have all my data back! I owe you one!

---

### Post by oldfred on 2012-05-16
Glad that worked.

And As my parents always said -  do as I say not as I do. - Back up frequently. :)

---

