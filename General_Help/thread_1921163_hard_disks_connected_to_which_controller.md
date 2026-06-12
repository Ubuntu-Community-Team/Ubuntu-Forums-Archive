---
title: "hard disks connected to which controller"
date: 2012-02-06
forum: General Help
---

### Post by Cyclane on 2012-02-06
Hi all,
 
Could you help me with the following:
 
I have 2 controllers, I can connect my SATA disks to and I have several hard disks. Now I wan't to know from within the OS, which disks are connected to which controller. I have no clue on how to perform this so could you pleaase help me.
 
Here is some generic info:
```

[SIZE=2][COLOR=#bf3030][SIZE=2][COLOR=#bf3030]linux-88nz:~ # [/COLOR][/SIZE][/COLOR][/SIZE][SIZE=2]lspci | grep -i sata[/SIZE]
[SIZE=2]00:11.0 [/SIZE][SIZE=2][COLOR=#bf3030][SIZE=2][COLOR=#bf3030]SATA[/COLOR][/SIZE][/COLOR][/SIZE][SIZE=2] controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 [/SIZE][SIZE=2][COLOR=#bf3030][SIZE=2][COLOR=#bf3030]SATA[/COLOR][/SIZE][/COLOR][/SIZE][SIZE=2] Controller [IDE mode][/SIZE]
[SIZE=2]03:00.0 SCSI storage controller: HighPoint Technologies, Inc. RocketRAID 230x 4 Port [/SIZE][SIZE=2][COLOR=#bf3030][SIZE=2][COLOR=#bf3030]SATA[/COLOR][/SIZE][/COLOR][/SIZE][SIZE=2]-II Controller (rev 02)[/SIZE]
[SIZE=2][COLOR=#bf3030][SIZE=2][COLOR=#bf3030]linux-88nz:~ # [/COLOR][/SIZE][/COLOR][/SIZE][SIZE=2]lsscsi[/SIZE]
[SIZE=2][1:0:0:0] disk ATA WDC WD10EARS-00M 51.0 /dev/sda[/SIZE]
[SIZE=2][2:0:0:0] disk ATA WDC WD10EARS-00M 51.0 /dev/sdb[/SIZE]
[SIZE=2][3:0:0:0] disk ATA WDC WD10EARS-00M 51.0 /dev/sdc[/SIZE]
[SIZE=2][4:0:0:0] disk TOSHIBA MK1059GSM 0100 /dev/sdd[/SIZE]
[SIZE=2][7:0:0:0] disk ATA ST31000528AS CC38 /dev/sde[/SIZE]
[SIZE=2][8:0:0:0] disk ATA WDC WD10EARS-00Y 80.0 /dev/sdf[/SIZE]

```

---

### Post by aasdfasdfg on 2012-02-06
I believe the information you are looking for can be found by querying sysfs. For a guide, see [here]("http://www.kernel.org/pub/linux/kernel/people/mochel/doc/papers/ols-2005/mochel.pdf")

---

