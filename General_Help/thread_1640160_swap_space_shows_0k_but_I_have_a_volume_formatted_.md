---
title: "swap space shows 0k but I have a volume formatted as swap..."
date: 2010-12-07
forum: General Help
---

### Post by emonti on 2010-12-07
Hi,

[U]Lucid on an Acer Travelmate800.
[/U]
Can anyone tell me why I have 0k for swap space? I allocated swap which I can see in my Disk Utility's 'volumes' display.

```
top - 18:19:05 up  7:46,  5 users,  load average: 1.32, 0.95, 0.72
Tasks: 173 total,   1 running, 172 sleeping,   0 stopped,   0 zombie
Cpu(s): 12.5%us,  7.0%sy,  0.0%ni, 80.5%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   1025984k total,   780588k used,   245396k free,    17016k buffers
Swap:        0k total,        0k used,        0k free,   133060k cached

```

---

### Post by sikander3786 on 2010-12-07
There seems some Swap being cached but it should also appear under 'total'.

Please post the output of these commands.

```
cat /etc/fstab
```

```
sudo blkid
```

```
free -m
```

---

### Post by emonti on 2010-12-07
Hi,

fstab:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc    /proc    proc    nodev,noexec,nosuid    0    0
#Entry for /dev/sda8 :
UUID=86517163-253e-45e2-9352-a87a8a639b2c    /    ext4    errors=remount-ro    0    1
#Entry for /dev/sda1 :
UUID=82A4DC8AA4DC8259    /media/winxp    ntfs-3g    defaults,locale=en_GB.utf8    0    0
#Entry for /dev/sda9 :
#UUID=ff5414e1-7dc6-4b1d-89fd-d25ac7d827cc    none    swap    sw    0    0
#//192.168.0.103/dev    /mnt/dev-on-netstat    cifs    iocharset=utf8,credentials=/home/jim/.smbcredentials-linux,gid=1000    0    0
UUID=fa62dc1c-f334-472e-9e2a-528a6d6d7036    none    swap    sw    0    0
//192.168.0.103/dev    /mnt/dev-on-netstat    cifs    iocharset=utf8,credentials=/home/jim/.smbcredentials-winxp,gid=1000    0    0

#//NETSTAT/dev    /mnt/dev-on-netstat    cifs    iocharset=utf8,credentials=/home/jim/.smbcredentials,uid=1000    0    0


```blkid:

```
/dev/sda1: UUID="82A4DC8AA4DC8259" TYPE="ntfs" 
/dev/sda5: UUID="cf1009e0-0d2d-4888-8946-816d89788c48" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda6: LABEL="New swap" UUID="ff5414e1-7dc6-4b1d-89fd-d25ac7d827cc" TYPE="swap" 
/dev/sda7: UUID="9ccf0e45-5c3a-4546-a953-b4d055271e26" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda8: UUID="86517163-253e-45e2-9352-a87a8a639b2c" TYPE="ext4" 
/dev/sda9: LABEL="ext4" UUID="da840263-6690-4d23-ace6-90b917d2deef" TYPE="ext4" 
/dev/sdb1: LABEL="FreeAgent GoFlex Drive" UUID="82FCAAEBFCAAD925" TYPE="ntfs" 
/dev/sdc1: LABEL="CORSAIR" UUID="44E1-67F7" TYPE="vfat" 
/dev/mapper/truecrypt1: UUID="4963-2C9D" TYPE="vfat" 

```free -m:

```
             total       used       free     shared    buffers     cached
Mem:          1001        973         28          0          6        130
-/+ buffers/cache:        836        164
Swap:            0          0          0

```thanks

---

### Post by gmargo on 2010-12-07
> 
```

#UUID=ff5414e1-7dc6-4b1d-89fd-d25ac7d827cc    none    swap    sw    0    0

```Your "new swap" entry is commented out.

> 
```

UUID=fa62dc1c-f334-472e-9e2a-528a6d6d7036    none    swap    sw    0    0

```This one is apparently your "old swap" since it doesn't appear in your blkid list.

So, uncomment the "new swap" and comment out the "old swap" entries.

---

### Post by emonti on 2010-12-07
Ah, makes sense.. I'll give that a shot.

Thanks.

---

### Post by emonti on 2010-12-09
Yes. 

'top' now shows the swap being used.

Thanks again for your time.

---

