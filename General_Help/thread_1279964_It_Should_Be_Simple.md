---
title: "It Should Be Simple?"
date: 2009-10-01
forum: General Help
---

### Post by rob2nd9th on 2009-10-01
It Should Be Simple? I want to copy my WOW files to a new computer, so I dont have to wait for the updates. 

But when i try i get this...

Error while copying "WoW-3.1.1.9806-to-3.1.1.9835-enGB-downloader.exe".
There was an error copying the file into /media/disk/World of Warcraft.
Error writing to file: Input/output error

Iv tried to copy the files from root but get the same?

Its on my HD I want to copy it to my eternal HD - It should be simple?
:(

---

### Post by StuartN on 2009-10-01
> **rob2nd9th said:**
> Its on my HD I want to copy it to my eternal HD

How big is your file? What filesystem are you copying from and to (use **mount** to check)?

---

### Post by arrange on 2009-10-01
Does *dmesg | tail* say something in more detail about the failed copy attempt?

---

### Post by rob2nd9th on 2009-10-01
total file's = 17.7 gb
External ha is 27gb free space.

---

### Post by StuartN on 2009-10-01
> **rob2nd9th said:**
> total file's = 17.7 gb
External ha is 27gb free space.

What filesystem? If any one file exceeds 4 GB then a FAT disk can not receive it.

---

### Post by rob2nd9th on 2009-10-01
> **StuartN said:**
> What filesystem? If any one file exceeds 4 GB then a FAT disk can not receive it.

I'm coping from a linux to linux machine and the ext hd is blank so whats the best filesystem to have?

(theres just over 100 files is there a quick way to see the size?)

---

### Post by StuartN on 2009-10-01
> **rob2nd9th said:**
> I'm coping from a linux to linux machine

But is the disk that you were copying to a FAT disk? If it is not FAT16 or FAT32 then your problem may be something else.

If you are only using the disk with Linux than EXT3 is good.

To list all files and sizes you can use **ls -lr** and scan through the output, or **find . -name "*" -size +1G** to list all files ("*") greater than one GigaByte (+1G) - anything over 4 GB would give an error on FAT but not EXT.

---

### Post by rob2nd9th on 2009-10-04
> **StuartN said:**
> But is the disk that you were copying to a FAT disk? If it is not FAT16 or FAT32 then your problem may be something else.

If you are only using the disk with Linux than EXT3 is good.

Ok formated external hard drive to EXT3, did not work same error on a file thats only - 15.9mb

Will work it out and post once iv sorted. (i hope)

---

### Post by arrange on 2009-10-04
Disconnect the external drive; then connect it back again. Post the output of```
dmesg | tail
mount
```

---

### Post by rob2nd9th on 2009-10-05
:~$ dmesg | tail
[   84.743607] scsi 5:0:0:0: Direct-Access     HTS42403 0M9AT00          0811 PQ: 0 ANSI: 0
[   84.774352] sd 5:0:0:0: [sdc] 58605120 512-byte hardware sectors: (30.0 GB/27.9 GiB)
[   84.777614] sd 5:0:0:0: [sdc] Test WP failed, assume Write Enabled
[   84.777618] sd 5:0:0:0: [sdc] Assuming drive cache: write through
[   84.778482] sd 5:0:0:0: [sdc] 58605120 512-byte hardware sectors: (30.0 GB/27.9 GiB)
[   84.780858] sd 5:0:0:0: [sdc] Test WP failed, assume Write Enabled
[   84.780860] sd 5:0:0:0: [sdc] Assuming drive cache: write through
[   84.780864]  sdc: sdc1 sdc2
[   85.133833] sd 5:0:0:0: [sdc] Attached SCSI disk
[   85.133905] sd 5:0:0:0: Attached scsi generic sg3 type 0



:~$ mount
/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.28-15-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
nfsd on /proc/fs/nfsd type nfsd (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/rob/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=rob)
/dev/sdc1 on /media/disk type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush)

the ext drive is back to fat32.

---

### Post by arrange on 2009-10-05
Looks pretty normal :)

Now - does creating a folder/file or saving to the disk appear to work normally, and it's just copying via Nautilus that is causing trouble?

---

### Post by rob2nd9th on 2009-10-05
Its fine normally.

Its the wow folder in wine that I wanted to back up so i did not need to run the up dates on my new machine.

---

### Post by tuahaa on 2009-10-05
well they shouldn't call it *fat* if it can only eat 4gb at a time...

---

