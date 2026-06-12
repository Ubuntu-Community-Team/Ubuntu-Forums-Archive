---
title: "/home filesystem suddenly goes readonly"
date: 2011-05-23
forum: General Help
---

### Post by lukiano on 2011-05-23
Hi,
I am a new Ubuntu user running Lucid Lynx and since some time suddenly my /home filesystem (mounted as ext3 on /dev/sda2) goes read-only... 
dmesg shows such a message...

```
[14097.976083] journal_bmap: journal block not found at offset 23564 on sda2
[14097.976087] Aborting journal on device sda2.
[14098.977188] ext3_abort called.
[14098.977194] EXT3-fs error (device sda2): ext3_journal_start_sb: Detected aborted journal
[14098.977198] Remounting filesystem read-only
```

Does anybody understand why this happen?
Is there a way to mount back the filesystem in the correct way without rebooting the system? I assume I won't be able to unmount the filesystem when I am logged on...

Thank you very much.
Luciano

---

### Post by anaconda on 2011-05-23
I dont think you can re-mount without booting.

Sounds like your disk is in need of checking
you can run fsck eg. from a liveCD

---

### Post by Grenage on 2011-05-23
The journal is having issues by the looks of it; I've never encountered this myself, but I have read of others removing the journal, running an e2fsck, then recreating the journal.  I'd probably start with just an e2fsck.

You will however want to back up any important data before you do this.

---

### Post by WorMzy on 2011-05-23
The first thing I recommend that you do is unmount and fsck it.
```
sudo umount /dev/sda2
sudo e2fsck -fcp /dev/sda2
```

I'd also like to check what options you're using with the partition in /etc/fstab, so paste the contents of that file here (in [CODE[COLOR="Black"]][[/COLOR]/CODE] tags please). Also, post the output of ```
sudo blkid
``` (again, in [CODE[COLOR="Black"]][[/COLOR]/CODE] tags)

---

### Post by philinux on 2011-05-23
> **lukiano said:**
> Hi,
I am a new Ubuntu user running Lucid Lynx and since some time suddenly my /home filesystem (mounted as ext3 on /dev/sda2) goes read-only... 
dmesg shows such a message...

[14097.976083] journal_bmap: journal block not found at offset 23564 on sda2
[14097.976087] Aborting journal on device sda2.
[14098.977188] ext3_abort called.
[14098.977194] EXT3-fs error (device sda2): ext3_journal_start_sb: Detected aborted journal
[14098.977198] Remounting filesystem read-only

Does anybody understand why this happen?
Is there a way to mount back the filesystem in the correct way without rebooting the system? I assume I won't be able to unmount the filesystem when I am logged on...

Thank you very much.
Luciano

I would run fsck from the live cd or usb. And check the smart data from system>admin>disk utlity.

```
sudo fsck -v /dev/sda2

```

---

### Post by lukiano on 2011-05-23
Thank you very much.
I already run e2fsck from a live CD but I couldn't fix the problem although something improved... Should I try again? What sort of options should I use?

---

### Post by satanselbow on 2011-05-23
Hey Lukiano,

No one has explicitly said here yet - but it is quite possible the your harddrive is failing and in need of replacement.

I would suggest that you get your data backed up onto another drive before you continue your repair attempts. This may, of course and hopefully, be purely a config problem that can be resolved with no loss of data but it is always better to keep things safe before you dive in ;) And attempting repairs on already faulty hardware does sometimes kill it altogether :(

---

### Post by lukiano on 2011-05-23
Thank you again. 
Fortunately I do not keep important data on that disk. I considered the worst scenario of a failing disk but I hope the disk can survive for some more time...
I will run the tests you suggested and let you know...

---

### Post by lukiano on 2011-05-23
The /etc/fstab file:
```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb4 during installation
UUID=c0b0c85e-6a1b-45d4-a446-54b4f0e2dc2f /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sdb3 during installation
UUID=6824a8ad-f346-4239-9179-d495f05185a7 /boot           ext3    defaults        0       2
# /dual was on /dev/sdb5 during installation
UUID=4808BB3208BB1E3E /dual           ntfs    defaults,nls=utf8,umask=007,gid=46 0       0
# /home was on /dev/sda2 during installation
UUID=098c786c-a4b8-4f7b-9f97-c370bca40a8e /home           ext3    defaults        0       2
# /windows was on /dev/sdb1 during installation
UUID=C8C0812EC08123B2 /windows        ntfs    defaults,nls=utf8,umask=007,gid=46 0       0
# swap was on /dev/sda3 during installation
UUID=4710fd6b-1ad9-4ec8-97de-eba70b584ed9 none            swap    sw              0       0
/dev/sda1       /zone        ext4 defaults 0 0
/dev/sdg        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
```

The blkid output:
```
/dev/sda1: LABEL="zone" UUID="92e96572-dc61-4506-b680-bd9c50aa151a" TYPE="ext4" 
/dev/sda2: UUID="098c786c-a4b8-4f7b-9f97-c370bca40a8e" TYPE="ext3" 
/dev/sda3: UUID="4710fd6b-1ad9-4ec8-97de-eba70b584ed9" TYPE="swap" 
/dev/sdb1: LABEL="Windows" UUID="C8C0812EC08123B2" TYPE="ntfs" 
/dev/sdb3: UUID="6824a8ad-f346-4239-9179-d495f05185a7" TYPE="ext3" 
/dev/sdb4: UUID="c0b0c85e-6a1b-45d4-a446-54b4f0e2dc2f" TYPE="ext4" 
/dev/sdb5: LABEL="Dual" UUID="4808BB3208BB1E3E" TYPE="ntfs" 
```

The Smart Data from the disk utility claim there is 1 bad sector and show a warning in the Current Pending Sector Count (ID 197)... To be sure I believe I should run this again after the fsck...

---

### Post by lukiano on 2011-05-25
e2fsck is running since more than 24 hours... I keep waiting for completion...

---

### Post by lukiano on 2011-06-20
Hi, I am back again...
After letting e2fsck run for more than a week I gave up... Since I had an identical disk, I decided to remove and change the drive and I cloned the content using clonezilla... The disk utility now sees a healthy disk but again every now and then the filesystem goes readonly...
Now if I unmount the partition and run e2fsck I manage to correct a few journal errors...
I am asking myself (but of course you will be able to answer better than me) if there is some software coming with Lynx (maybe wrongly installed) which can cause something like this...
Thank you again for yor help...

---

