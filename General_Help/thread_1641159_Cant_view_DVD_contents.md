---
title: "Cant view DVD contents"
date: 2010-12-08
forum: General Help
---

### Post by mattgyver83 on 2010-12-08
Hey all, any help would be greatly appreciated.

I backed up about 19GB of my Web Server today compressed into a .tar.gz.  I then split these files into 4300MB chunks (approx 4.2GB).  I then used k3b to write 2 parts of the archive these to a Dual Layer DVD.  The burn went fine but I cannot seem to mount said DVD.  I tried the following;

```

matt@matt-u:/media$ sudo mount -t udf /dev/sr0 /media/cd
mount: block device /dev/sr0 is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/sr0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

matt@matt-u:/media$ 

```

```

matt@matt-u:/media$ dmesg | tail
[16515.428259] sr 4:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[16515.428269] sr 4:0:0:0: [sr0] CDB: Read(10): 28 00 00 46 26 7f 00 00 01 00
[16515.428286] end_request: I/O error, dev sr0, sector 18389500
[16515.430102] sr 4:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[16515.430109] sr 4:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[16515.430117] sr 4:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[16515.430127] sr 4:0:0:0: [sr0] CDB: Read(10): 28 00 00 46 27 b7 00 00 01 00
[16515.430143] end_request: I/O error, dev sr0, sector 18390748
[16515.430165] UDF-fs: No anchor found
[16515.430173] UDF-fs: No partition found (1)
matt@matt-u:/media$ 

```

Any ideas?

---

### Post by dcstar on 2010-12-08
> **mattgyver83 said:**
> Hey all, any help would be greatly appreciated.

I backed up about 19GB of my Web Server today compressed into a .tar.gz.  I then split these files into 4300MB chunks (approx 4.2GB).  I then used k3b to write 2 parts of the archive these to a Dual Layer DVD.  The burn went fine but I cannot seem to mount said DVD.  I tried the following;

```

matt@matt-u:/media$ sudo mount **-t udf **/dev/sr0 /media/cd
mount: block device /dev/sr0 is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/sr0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

matt@matt-u:/media$ 

```

```

matt@matt-u:/media$ dmesg | tail
[16515.428259] sr 4:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[16515.428269] sr 4:0:0:0: [sr0] CDB: Read(10): 28 00 00 46 26 7f 00 00 01 00
[16515.428286] end_request: **I/O error, dev sr0, sector 18389500**
[16515.430102] sr 4:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[16515.430109] sr 4:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[16515.430117] sr 4:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[16515.430127] sr 4:0:0:0: [sr0] CDB: Read(10): 28 00 00 46 27 b7 00 00 01 00
[16515.430143] end_request: **I/O error, dev sr0, sector 18390748**
[16515.430165] UDF-fs: No anchor found
[16515.430173] UDF-fs: No partition found (1)
matt@matt-u:/media$ 

```

Any ideas?

[LIST=1]
[*]Why not allow the mount to auto-detect the partition type?
[*]If it says I/O errors, then it cannot read those areas.
[/LIST]

---

### Post by mattgyver83 on 2010-12-09
Hey dave thanks for the reply.  I tried to let it auto-detect but it gave me an error telling me i needed to specify the FS type so thats why i used -t udf.  I noticed the I/O errors but wasnt sure if that was because it was getting that because the tracks were bad, or if it was due to maybe me not mounting it properly.

Ill just give it another go and see what that joker does.  Thanks.

---

