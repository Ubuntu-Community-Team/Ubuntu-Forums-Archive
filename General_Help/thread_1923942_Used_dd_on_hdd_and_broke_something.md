---
title: "Used dd on hdd and broke something"
date: 2012-02-11
forum: General Help
---

### Post by brandon88tube on 2012-02-11
I probably did something wrong, but I was trying to write an iso to my hdd with dd and after doing so I lost all of the space on it equivalent to that of the iso's size. The drive no longer comes up with the correct drive info and it says there is an error with the partition table. I can't reformat it or anything. I would like some help to try and fix it and I don't care if I have to wipe it or anything.

---

### Post by josephmills on 2012-02-11
please open your terminal and type in 
```
sudo fdisk -l && df -h && lsmod 
```
and paste here thanks

---

### Post by winh8r on 2012-02-11
post retracted.

---

### Post by brandon88tube on 2012-02-11
This is on another machine so I have to copy the output over to this one.
```

ubuntu@ubuntu:~$ sudo fdisk -l && df -h && lsmod

Disk /dev/sda: 7530 MB, 7530356736 bytes
255 heads, 63 sectors/track, 915 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/sda doesn't contain a valid partition table

Disk /dev/sdb: 1941 MB, 1941180416 bytes
60 heads, 62 sectors/track, 1019 cylinders
Units = cylinders of 3720 * 512 = 1904640 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000afd17

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1019     1895309    c  W95 FAT32 (LBA)
Filesystem            Size  Used Avail Use% Mounted on
aufs                  1.5G  6.2M  1.5G   1% /
none                  1.5G  280K  1.5G   1% /dev
/dev/sdb1             1.9G  1.2G  707M  62% /cdrom
/dev/loop0            658M  658M     0 100% /rofs
none                  1.5G  1.2M  1.5G   1% /dev/shm
tmpfs                 1.5G   12K  1.5G   1% /tmp
none                  1.5G   80K  1.5G   1% /var/run
none                  1.5G     0  1.5G   0% /var/lock
none                  1.5G     0  1.5G   0% /lib/init/rw
Module                  Size  Used by
binfmt_misc             6587  1 
lp                      7028  0 
dm_crypt               11331  0 
snd_hda_codec_realtek   203310  1 
snd_hda_intel          21941  2 
snd_hda_codec          74201  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70662  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26726  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    54148  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
ppdev                   5259  0 
parport_pc             25962  1 
soundcore               6620  1 snd
parport                32635  3 lp,ppdev,parport_pc
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
squashfs               20680  1 
aufs                  149050  1 
nls_iso8859_1           3249  1 
nls_cp437               4919  1 
vfat                    8933  1 
fat                    47767  1 vfat
dm_raid45              81647  0 
xor                    15028  1 dm_raid45
fbcon                  35102  71 
tileblit                2031  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  0 
vgastate                8961  1 vga16fb
nouveau               467048  2 
usbhid                 36110  0 
hid                    67032  1 usbhid
usb_storage            39425  1 
ttm                    49943  1 nouveau
drm_kms_helper         29297  1 nouveau
floppy                 53016  0 
pata_jmicron            1843  0 
drm                   162377  4 nouveau,ttm,drm_kms_helper
r8169                  34076  0 
mii                     4381  1 r8169
intel_agp              24119  0 
agpgart                31724  3 ttm,drm,intel_agp
i2c_algo_bit            5028  1 nouveau


```

---

### Post by dcstar on 2012-02-11
> **brandon88tube said:**
> I probably did something wrong, but I was trying to write an iso to my hdd with dd and after doing so I lost all of the space on it equivalent to that of the iso's size. The drive no longer comes up with the correct drive info and it says there is an error with the partition table. I can't reformat it or anything. I would like some help to try and fix it and **I don't care if I have to wipe it or anything**.

Boot off a Live CD/USB and use **gparted** to write a new Partition Table to it.

---

### Post by brandon88tube on 2012-02-11
To be more specific, gparted seems like it is creating a partition table, but it never really does and complains that I need to create one. When I try diskutility, it just fails with an error. Either way isn't working and my system no longer sees it as 10gb, but instead 7gb. The device info now reports "Haxthr" instead of "Maxtor".

---

### Post by sleepyhollows on 2012-02-12
> **brandon88tube said:**
> 
The device info now reports "Haxthr" instead of "Maxtor".

Nice work! 

No idea though

---

### Post by brandon88tube on 2012-02-12
Anyone have any ideas? I would hate to think that I irreversibly ruined my hdd just by using dd.

---

### Post by Dave_L on 2012-02-12
You could try testdisk; it may have repair options that gparted lacks.

Testdisk, as well as gparted and other tools, is available on the SystemRescueCD: [http://www.sysresccd.org/](http://www.sysresccd.org/)

---

