---
title: "mount manager, mount image problem, startup problem"
date: 2011-09-14
forum: General Help
---

### Post by rwakc on 2011-09-14
Hi,
I will tell you step by step what I did

1. installed virtualBox
2. installed MountManager
3. tried to mount .iso file(since it would not mount with archive manager due to udf)

So when I found out, that MountManager did not mount my image right I uninstalled it. But now I have this problem. It keeps mounting to mount point I selected before - in my case [HTML]/media/New[/HTML] My system would not even boot up if I do not press the "S" button, so that I skip mounting of that volume(I found that out in recovery mode). And it does that every time I restart my computer.

I tried installing mount manager again and tried to unmount it, but I could not.

Then I saw it made a huge mess from my /etc/fstab so I read the manual on understanding fstab which after my edit looks like that:

```
UUID=12A6C69AA6C67E2B                      /media/New Volume        ntfs-3g  defaults                           0  0
UUID=C8CC0E15CC0DFE86                      /media/C8CC0E15CC0DFE86  ntfs-3g  defaults                           0  0  
UUID=cce7f0ae-84df-4032-84c5-b23b8f00bd59  /swap                    swap     defaults                           0  0  
UUID=005be718-1c5a-4515-b5e9-ddf96a9b06c9  /                        ext4     defaults                           0  1  
/dev/sdb2                                  /media/sdb2              ntfs     nls=iso8859-1,ro,umask=000         0  0  
/dev/sda2                                  /media/sda2              ntfs     defaults                           0  0  
/dev/sdb1                                  /media/sdb1              ntfs     nls=iso8859-1,ro,noauto,umask=000  0  0  
```

Well, my system still wont boot up and the error message I get in recovery mode is
[HTML]Mountall: Filesystem could not be mounted /media/New [/HTML]

And I believe it has nothing to do with my New Volume disk since my directory view of /media looks like that
[HTML]2A6A81066A80D04D  C8CC0E15CC0DFE86  E469-31B7  New  sda2  sdb1	sdb2
[/HTML] and I tried running nautilus as a superuser and deleting the '/media/New' folder, but it was created again at next reboot.

Lists:

ls /dev/disk/by-label -lah

```

total 0
drwxr-xr-x 2 root root  80 2011-09-14 15:39 .
drwxr-xr-x 6 root root 120 2011-09-14 17:05 ..
lrwxrwxrwx 1 root root  10 2011-09-14 15:05 New\x20Volume -> ../../sda2
lrwxrwxrwx 1 root root  10 2011-09-14 15:39 Recovery -> ../../sdb1

```

ls /dev/disk/by-id -lah
```

total 0
drwxr-xr-x 2 root root 400 2011-09-14 15:39 .
drwxr-xr-x 6 root root 120 2011-09-14 17:05 ..
lrwxrwxrwx 1 root root   9 2011-09-14 15:05 ata-MATSHITABD-MLT_UJ-220S_HC51_095207 -> ../../sr0
lrwxrwxrwx 1 root root   9 2011-09-14 15:39 ata-ST9200420AS_5SH04X2R -> ../../sda
lrwxrwxrwx 1 root root  10 2011-09-14 15:39 ata-ST9200420AS_5SH04X2R-part1 -> ../../sda1
lrwxrwxrwx 1 root root  10 2011-09-14 15:05 ata-ST9200420AS_5SH04X2R-part2 -> ../../sda2
lrwxrwxrwx 1 root root  10 2011-09-14 15:39 ata-ST9200420AS_5SH04X2R-part3 -> ../../sda3
lrwxrwxrwx 1 root root  10 2011-09-14 15:05 ata-ST9200420AS_5SH04X2R-part4 -> ../../sda4
lrwxrwxrwx 1 root root  10 2011-09-14 15:05 ata-ST9200420AS_5SH04X2R-part5 -> ../../sda5
lrwxrwxrwx 1 root root   9 2011-09-14 15:39 scsi-SATA_ST9200420AS_5SH04X2R -> ../../sda
lrwxrwxrwx 1 root root  10 2011-09-14 15:39 scsi-SATA_ST9200420AS_5SH04X2R-part1 -> ../../sda1
lrwxrwxrwx 1 root root  10 2011-09-14 15:05 scsi-SATA_ST9200420AS_5SH04X2R-part2 -> ../../sda2
lrwxrwxrwx 1 root root  10 2011-09-14 15:39 scsi-SATA_ST9200420AS_5SH04X2R-part3 -> ../../sda3
lrwxrwxrwx 1 root root  10 2011-09-14 15:05 scsi-SATA_ST9200420AS_5SH04X2R-part4 -> ../../sda4
lrwxrwxrwx 1 root root  10 2011-09-14 15:05 scsi-SATA_ST9200420AS_5SH04X2R-part5 -> ../../sda5
lrwxrwxrwx 1 root root   9 2011-09-14 15:39 usb-FUJITSU_MHX2300BT_M6116A016V20-0:0 -> ../../sdb
lrwxrwxrwx 1 root root  10 2011-09-14 15:39 usb-FUJITSU_MHX2300BT_M6116A016V20-0:0-part1 -> ../../sdb1
lrwxrwxrwx 1 root root  10 2011-09-14 15:20 usb-FUJITSU_MHX2300BT_M6116A016V20-0:0-part2 -> ../../sdb2
lrwxrwxrwx 1 root root   9 2011-09-14 15:49 usb-_Patriot_Memory_07971008E5BA1060-0:0 -> ../../sdc
lrwxrwxrwx 1 root root  10 2011-09-14 15:49 usb-_Patriot_Memory_07971008E5BA1060-0:0-part1 -> ../../sdc1

```

ls /dev/disk/by-uuid -lah
```

total 0
drwxr-xr-x 2 root root 180 2011-09-14 15:39 .
drwxr-xr-x 6 root root 120 2011-09-14 17:05 ..
lrwxrwxrwx 1 root root  10 2011-09-14 15:05 005be718-1c5a-4515-b5e9-ddf96a9b06c9 -> ../../sda4
lrwxrwxrwx 1 root root  10 2011-09-14 15:05 12A6C69AA6C67E2B -> ../../sda2
lrwxrwxrwx 1 root root  10 2011-09-14 15:20 2A6A81066A80D04D -> ../../sdb2
lrwxrwxrwx 1 root root  10 2011-09-14 15:39 524E7D9E4E7D7C13 -> ../../sdb1
lrwxrwxrwx 1 root root  10 2011-09-14 15:39 C8CC0E15CC0DFE86 -> ../../sda1
lrwxrwxrwx 1 root root  10 2011-09-14 15:05 cce7f0ae-84df-4032-84c5-b23b8f00bd59 -> ../../sda5
lrwxrwxrwx 1 root root  10 2011-09-14 15:49 E469-31B7 -> ../../sdc1

```

---

