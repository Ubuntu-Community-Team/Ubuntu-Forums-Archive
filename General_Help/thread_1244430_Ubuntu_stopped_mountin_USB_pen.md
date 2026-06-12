---
title: "Ubuntu stopped mountin USB pen"
date: 2009-08-19
forum: General Help
---

### Post by trozombo on 2009-08-19
Here i am consulting once again tha mighty ubuntu forum.
my problems the next. Suddenly ubuntu stopped mountin my 1 gi usb pen.
there are no problems with the actual as i transferred files via ubuntu live.
 herere some outputs:

```
roberto@roberto-laptop:~$ dmesg|tail
[  254.965054] sd 2:0:0:0: [sdb] Mode Sense: 0b 00 00 08
[  254.965062] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[  254.967436] sd 2:0:0:0: [sdb] 2054144 512-byte hardware sectors: (1.05 GB/1003 MiB)
[  254.970263] sd 2:0:0:0: [sdb] Write Protect is off
[  254.970273] sd 2:0:0:0: [sdb] Mode Sense: 0b 00 00 08
[  254.970280] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[  254.970293]  sdb: sdb1
[  254.971727] sd 2:0:0:0: [sdb] Attached SCSI removable disk
[  254.971903] sd 2:0:0:0: Attached scsi generic sg2 type 0
[  255.628611] FAT: codepage cp437 not found
roberto@roberto-laptop:~$ 
```and

```
roberto@roberto-laptop:~$ sudo fdisk -l
[sudo] password for roberto: 

Disco /dev/sda: 40.0 GB, 40007761920 byte
255 testine, 63 settori/tracce, 4864 cilindri
Unità = cilindri di 16065 * 512 = 8225280 byte
Identificativo disco: 0x9dc96e9e

Dispositivo Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1318    10586803+  83  Linux
/dev/sda2   *        1319        4659    26836582+   7  HPFS/NTFS
/dev/sda3            4660        4864     1646662+   5  Esteso
/dev/sda5            4660        4864     1646631   82  Linux swap / Solaris

Disco /dev/sdb: 1051 MB, 1051721728 byte
2 testine, 63 settori/tracce, 16302 cilindri
Unità = cilindri di 126 * 512 = 64512 byte
Identificativo disco: 0x00ef38e7

Dispositivo Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       16303     1027056    b  W95 FAT32
```and 

> roberto@roberto-laptop:~$ mount
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
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/roberto/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=roberto)
/dev/sda2 on /media/disk type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)

the actual error is

  mount: wrong fs type, bad option, bad superblock / dev/sdb1, missing codepage or helper
[IMG]http://yfrog.com/09schermataqj[/IMG]
[IMG]http://yfrog.com/09schermataqj[/IMG]could it be that it went wrong because i unplugged it without unmounting??
the key is formatted in fat 32 with gparted.


any ideas????

---

### Post by trozombo on 2009-08-19
just realized trying to launch simcity 4 that wouldnt mount this cd neither.
eroor is:
the system file ISO9660 is not supported on this system,

WTF!!!! i played till last night an no problm whatsoever.......

---

### Post by trozombo on 2009-08-19
been reading around and noticed that mounting is managed by etc/fstab
well  mine looks pretty different to others ive seen in the net:

```
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda3 during installation
UUID=e5abfa50-7596-4bc7-bfe2-01dad00dbeba /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=c8d2b79e-9121-4946-b8cc-4b6f778c48b6 none            swap    sw              0   0

```

is there any model to fix this voice???

---

### Post by trozombo on 2009-08-20
this is seriuosly doing my head in .......
i dont seem to get a proper answer from anywhere 
doe it mean i have to do a fresh install???
this is dissapointing...cant carry on with 
a system that doesnt read cds anymore....

---

