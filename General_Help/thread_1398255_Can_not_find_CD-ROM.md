---
title: "Can not find CD-ROM?"
date: 2010-02-04
forum: General Help
---

### Post by wzw_234 on 2010-02-04
I installed ubuntu 9.10 with CD&#65292;then update softwares and install Vmware Workstation 7.
However after my restarting computer, ubuntu can not find CD-ROM
I'm fresh. What should I do? Thanks!

Waring:
Unable to mount location
mount: special device /dev/scd0 does not exist

System information:

ls /dev&#65306;
adsp             lp0                 ram9        tty19  tty48    usbmon6
agpgart          mapper              random      tty2   tty49    usbmon7
audio            mcelog              rfkill      tty20  tty5     usbmon8
binder           mem                 rtc         tty21  tty50    vcs
block            mixer               rtc0        tty22  tty51    vcs1
bus              net                 sda         tty23  tty52    vcs2
char             network_latency     sda1        tty24  tty53    vcs3
console          network_throughput  sda3        tty25  tty54    vcs4
core             null                sda5        tty26  tty55    vcs5
cpu_dma_latency  oldmem              sda6        tty27  tty56    vcs6
disk             parport0            sequencer   tty28  tty57    vcs7
dri              pktcdvd             sequencer2  tty29  tty58    vcs8
dsp              port                sg0         tty3   tty59    vcsa
ecryptfs         ppp                 shm         tty30  tty6     vcsa1
fb0              psaux               snapshot    tty31  tty60    vcsa2
fd               ptmx                snd         tty32  tty61    vcsa3
full             pts                 sndstat     tty33  tty62    vcsa4
fuse             ram0                stderr      tty34  tty63    vcsa5
heci             ram1                stdin       tty35  tty7     vcsa6
hidraw0          ram10               stdout      tty36  tty8     vcsa7
hpet             ram11               tty         tty37  tty9     vcsa8
input            ram12               tty0        tty38  ttyS0    vmci
kmsg             ram13               tty1        tty39  ttyS1    vmmon
log              ram14               tty10       tty4   ttyS2    vmnet0
loop0            ram15               tty11       tty40  ttyS3    vmnet1
loop1            ram2                tty12       tty41  urandom  vmnet8
loop2            ram3                tty13       tty42  usbmon0  vsock
loop3            ram4                tty14       tty43  usbmon1  zero
loop4            ram5                tty15       tty44  usbmon2
loop5            ram6                tty16       tty45  usbmon3
loop6            ram7                tty17       tty46  usbmon4
loop7            ram8                tty18       tty47  usbmon5

fstab&#65306;
proc            /proc           proc    defaults        0       0
UUID=e2067c05-880f-4caa-a391-f40c082645b5 /               ext4    errors=remount-ro 0       1
UUID=f7852587-efe4-4a56-aa6a-ca17f91e239c /home           ext4    defaults        0       2
UUID=1AB9-7AF0  /windows        vfat    utf8,umask=007,gid=46 0       1
UUID=0b6b65db-8533-4488-98d8-eba9d06cb8b9 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

ls -al /media&#65306;
total 12
drwxr-xr-x  3 root root 4096 2010-02-04 03:17 .
drwxr-xr-x 23 root root 4096 2010-02-04 03:52 ..
lrwxrwxrwx  1 root root    6 2010-02-03 19:36 cdrom -> cdrom0
drwxr-xr-x  2 root root 4096 2010-02-03 19:36 cdrom0

sudo lshw -c disk&#65306;
  *-disk                  
       description: ATA Disk
       product: Hitachi HDP72502
       vendor: Hitachi
       physical id: 0.0.0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
       version: GM2O
       serial: GEK260RH29UKNA
       size: 232GiB (250GB)
       configuration: ansiversion=5 signature=00081c5d

lsusb&#65306;
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 002: ID 046d:c016 Logitech, Inc. M-UV69a/HP M-UV96 Optical Wheel Mouse
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

sudo mount&#65306;
/dev/sda1 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/dev/sda3 on /windows type vfat (rw,utf8,umask=007,gid=46)
/dev/sda6 on /home type ext4 (rw)
none on /proc/fs/vmblock/mountPoint type vmblock (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/fouc/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=fouc)

---

