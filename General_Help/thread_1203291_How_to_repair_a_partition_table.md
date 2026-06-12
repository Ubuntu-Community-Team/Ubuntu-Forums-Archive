---
title: "How to repair a partition table?"
date: 2009-07-03
forum: General Help
---

### Post by jrz on 2009-07-03
While copying files to an ext3 USB drive I received an error message that the drive could not be written to, and it had unmounted. Remounting it was no longer possible and it appears that sector 0 is corrupted. When attempting to mount the drive all that happens is an entry appears in /dev for sdb, but not partition sdb1. Gparted does not recognize the drive nor any other command I can think of. Is there a tool which can be used to manually repair the partition table? I have over 200 GB of data I wouldlike to retrieve.

---

### Post by WitchCraft on 2009-07-03
> **jrz said:**
> While copying files to an ext3 USB drive I received an error message that the drive could not be written to, and it had unmounted. Remounting it was no longer possible and it appears that sector 0 is corrupted. When attempting to mount the drive all that happens is an entry appears in /dev for sdb, but not partition sdb1. Gparted does not recognize the drive nor any other command I can think of. Is there a tool which can be used to manually repair the partition table? I have over 200 GB of data I wouldlike to retrieve.

fsck -t ext3 /dev/sdX1

Good luck!

---

### Post by jrz on 2009-07-03
I tried that and get the following output:

dmesg when the drive is first mounted:

[92034.240086] usb 1-3: new high speed USB device using ehci_hcd and address 4
[92039.610501] usb 1-3: configuration #1 chosen from 1 choice
[92039.656425] scsi4 : SCSI emulation for USB Mass Storage devices
[92039.661563] usb-storage: device found at 4
[92039.661571] usb-storage: waiting for device to settle before scanning
[92044.660338] usb-storage: device scan complete
[92044.664808] scsi 4:0:0:0: Direct-Access     WDC WD50 00AAKS-00A7B0         PQ: 0 ANSI: 2
[92044.669898] sd 4:0:0:0: [sdb] 976773168 512-byte hardware sectors: (500 GB/465 GiB)
[92044.725579] sd 4:0:0:0: [sdb] Write Protect is off
[92044.725592] sd 4:0:0:0: [sdb] Mode Sense: 38 00 00 00
[92044.725599] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[92044.726631] sd 4:0:0:0: [sdb] 976773168 512-byte hardware sectors: (500 GB/465 GiB)
[92044.730268] sd 4:0:0:0: [sdb] Write Protect is off
[92044.730278] sd 4:0:0:0: [sdb] Mode Sense: 38 00 00 00
[92044.730285] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[92044.730299]  sdb: sdb1
[92044.748435] sd 4:0:0:0: [sdb] Attached SCSI disk
[92044.748621] sd 4:0:0:0: Attached scsi generic sg2 type 0
joe@ibm:~$ 


joe@ibm:~$ sudo fsck -t ext3 /dev/sdb1
[sudo] password for joe: 
fsck 1.41.4 (27-Jan-2009)
e2fsck 1.41.4 (27-Jan-2009)
fsck.ext3: Attempt to read block from filesystem resulted in short read while trying to open /dev/sdb1
Could this be a zero-length partition?
joe@ibm:~$

dmesg after running the fsck:

[92184.722058] sd 4:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[92184.722074] sd 4:0:0:0: [sdb] Sense Key : Aborted Command [current] 
[92184.722087] sd 4:0:0:0: [sdb] Add. Sense: Scsi parity error
[92184.722103] end_request: I/O error, dev sdb, sector 63
[92184.722114] __ratelimit: 23 callbacks suppressed
[92184.722123] Buffer I/O error on device sdb1, logical block 0
[92184.722135] Buffer I/O error on device sdb1, logical block 1
[92184.722144] Buffer I/O error on device sdb1, logical block 2
[92184.722152] Buffer I/O error on device sdb1, logical block 3
[92184.722165] Buffer I/O error on device sdb1, logical block 4
[92184.722174] Buffer I/O error on device sdb1, logical block 5
[92184.722182] Buffer I/O error on device sdb1, logical block 6
[92184.722190] Buffer I/O error on device sdb1, logical block 7
[92184.722199] Buffer I/O error on device sdb1, logical block 8
[92184.722208] Buffer I/O error on device sdb1, logical block 9
[92184.924653] sd 4:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[92184.924669] sd 4:0:0:0: [sdb] Sense Key : Aborted Command [current] 
[92184.924682] sd 4:0:0:0: [sdb] Add. Sense: Scsi parity error
[92184.924698] end_request: I/O error, dev sdb, sector 63
joe@ibm:~$

---

### Post by WitchCraft on 2009-07-04
> **jrz said:**
> I tried that and get the following output:

dmesg when the drive is first mounted:

[92034.240086] usb 1-3: new high speed USB device using ehci_hcd and address 4
[92039.610501] usb 1-3: configuration #1 chosen from 1 choice
[92039.656425] scsi4 : SCSI emulation for USB Mass Storage devices
[92039.661563] usb-storage: device found at 4
[92039.661571] usb-storage: waiting for device to settle before scanning
[92044.660338] usb-storage: device scan complete
[92044.664808] scsi 4:0:0:0: Direct-Access     WDC WD50 00AAKS-00A7B0         PQ: 0 ANSI: 2
[92044.669898] sd 4:0:0:0: [sdb] 976773168 512-byte hardware sectors: (500 GB/465 GiB)
[92044.725579] sd 4:0:0:0: [sdb] Write Protect is off
[92044.725592] sd 4:0:0:0: [sdb] Mode Sense: 38 00 00 00
[92044.725599] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[92044.726631] sd 4:0:0:0: [sdb] 976773168 512-byte hardware sectors: (500 GB/465 GiB)
[92044.730268] sd 4:0:0:0: [sdb] Write Protect is off
[92044.730278] sd 4:0:0:0: [sdb] Mode Sense: 38 00 00 00
[92044.730285] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[92044.730299]  sdb: sdb1
[92044.748435] sd 4:0:0:0: [sdb] Attached SCSI disk
[92044.748621] sd 4:0:0:0: Attached scsi generic sg2 type 0
joe@ibm:~$ 


joe@ibm:~$ sudo fsck -t ext3 /dev/sdb1
[sudo] password for joe: 
fsck 1.41.4 (27-Jan-2009)
e2fsck 1.41.4 (27-Jan-2009)
fsck.ext3: Attempt to read block from filesystem resulted in short read while trying to open /dev/sdb1
Could this be a zero-length partition?
joe@ibm:~$

dmesg after running the fsck:

[92184.722058] sd 4:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[92184.722074] sd 4:0:0:0: [sdb] Sense Key : Aborted Command [current] 
[92184.722087] sd 4:0:0:0: [sdb] Add. Sense: Scsi parity error
[92184.722103] end_request: I/O error, dev sdb, sector 63
[92184.722114] __ratelimit: 23 callbacks suppressed
[92184.722123] Buffer I/O error on device sdb1, logical block 0
[92184.722135] Buffer I/O error on device sdb1, logical block 1
[92184.722144] Buffer I/O error on device sdb1, logical block 2
[92184.722152] Buffer I/O error on device sdb1, logical block 3
[92184.722165] Buffer I/O error on device sdb1, logical block 4
[92184.722174] Buffer I/O error on device sdb1, logical block 5
[92184.722182] Buffer I/O error on device sdb1, logical block 6
[92184.722190] Buffer I/O error on device sdb1, logical block 7
[92184.722199] Buffer I/O error on device sdb1, logical block 8
[92184.722208] Buffer I/O error on device sdb1, logical block 9
[92184.924653] sd 4:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[92184.924669] sd 4:0:0:0: [sdb] Sense Key : Aborted Command [current] 
[92184.924682] sd 4:0:0:0: [sdb] Add. Sense: Scsi parity error
[92184.924698] end_request: I/O error, dev sdb, sector 63
joe@ibm:~$

Your /dev/sdb1 superblock may be corrupted. 
If so, you need to try to do e2fsck using an alternative superblock. 

Try sudo mke2fs -t ext3 -n /dev/sdb1 
which from what I understand should tell you where the backup superblocks are stored.

> 
NAME
       mke2fs - create an ext2/ext3 filesystem


     -n     Causes mke2fs to not actually create a filesystem,  but  display
              what it would do if it were to create a filesystem.  This can be
              used to determine the location of the backup superblocks  for  a
              particular  filesystem,  so  long  as the mke2fs parameters that
              were passed when the filesystem was originally created are  used
              again.  (With the -n option added, of course!)



Output should look something like this:
> 
all:~# mke2fs -t swap -n /dev/hda5
mke2fs 1.41.3 (12-Oct-2008)
Filesystem label=
OS type: Linux
Block size=4096 (log=2)
Fragment size=4096 (log=2)
166320 inodes, 664681 blocks
33234 blocks (5.00%) reserved for the super user
First data block=0
Maximum filesystem blocks=683671552
21 block groups
32768 blocks per group, 32768 fragments per group
7920 inodes per group
Superblock backups stored on blocks: 
	32768, 98304, 163840, 229376, 294912



With the data above, you would run: sudo e2fsck -b 32768 /dev/hda5

---

### Post by jrz on 2009-07-06
Running the mke2fs command produces:

joe@ibm:~$ sudo mke2fs -t ext3 -n /dev/sdb1
[sudo] password for joe: 
mke2fs 1.41.4 (27-Jan-2009)
Filesystem label=
OS type: Linux
Block size=4096 (log=2)
Fragment size=4096 (log=2)
30531584 inodes, 122096000 blocks
6104800 blocks (5.00%) reserved for the super user
First data block=0
Maximum filesystem blocks=0
3727 block groups
32768 blocks per group, 32768 fragments per group
8192 inodes per group
Superblock backups stored on blocks: 
	32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632, 2654208, 
	4096000, 7962624, 11239424, 20480000, 23887872, 71663616, 78675968, 
	102400000

Do I need to run the e2fsck command on each number shown in "Superblock backups stored on blocks:" ? 

And most importantly, will I be able to retrieve my files or will everything be lost?

Thanks very much for the help.

---

### Post by WitchCraft on 2009-07-07
> **jrz said:**
> 
Do I need to run the e2fsck command on each number shown in "Superblock backups stored on blocks:" ? 

It depends on how much has been corrupted.
Basically, I would start with the first, and if that doesn't yield any result, try the next, and so on...


> **jrz said:**
> 
And most importantly, will I be able to retrieve my files or will everything be lost?

Thanks very much for the help.

The retrieved files you will find in the folder "lost+found".
Depends on how lucky you are and on how correct the parameters are.

If you're lucky, then there is the chance that you might retrieve everything or at least much, but you'll probably better get accustomed to the fact that you most likely have lost everything.


Maybe you should ask some more people whether they have a better idea...

I don't know too much about the Linux filesystems, or how best to retrieve it, but maybe you should send an mail to Valérie Henson, you find her e-mail at her personal homepage ([http://valerieaurora.org/](http://valerieaurora.org/))

She certainly knows about the Linux filesystems, and maybe (if you ask very kindly) she can help you further.

Good luck !

PS: Next time, take the time to learn the Linux mantra: backup to /dev/null saves time, but not data !

---

