---
title: "swap .. issus"
date: 2009-11-20
forum: General Help
---

### Post by alz3abi on 2009-11-20
hello every body .. 


i have install ubuntu without use swap partition .. after ubuntu use .. i do add swap partition . 

but no thing of thats swap used !

```
hz@hz:~$ free
             total       used       free     shared    buffers     cached
Mem:       3087768    1395528    1692240          0      75872     843108
-/+ buffers/cache:     476548    2611220
Swap:      1046520          0    1046520

``````
hz@hz:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x7153ad3b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        8509    68348511    7  HPFS/NTFS
/dev/sda2            8510       19457    87939810    f  W95 Ext'd (LBA)
/dev/sda5            8510       17368    71155535    7  HPFS/NTFS
/dev/sda6           17368       17498     1046528   82  Linux swap / Solaris
/dev/sda7           17499       19457    15735636   83  Linux
``````
hz@hz:~$ cat /proc/swaps
Filename                Type        Size          Used    Priority
/dev/sda6               partition   1046520    0         -1

```

i ran alot programs ! open office (all programs). Gaimp .. and alot . but swap still 0 usage. 


more info. 
```
hz@hz:~$ cat /proc/sys/vm/swappiness
10
```

/etc/fstab content. 

```
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda6 during installation
UUID=50c6f432-87be-420a-a8c9-88771aa07b66 /               ext4    relatime,errors=remount-ro 0       1
/dev/sda6  none  swap  sw  0 0
```

any help please :)

with best regards ;)

---

### Post by emigrant on 2009-11-20
run gparted and right click on the swap and give 'swap on'

---

### Post by ncmncm on 2009-11-20
Please read  the initial notes on swap. 

Swap is used when you have used up _available memory_. When you have  very large RAM, it makes sense for the OS to use it from RAM as opposed to reading from  the hardisk ( slower).

You have 3GB of RAM and only 30% of it used.

---

### Post by alz3abi on 2009-11-20
> **emigrant said:**
> run gparted and right click on the swap and give 'swap on'
swap already active 
[ATTACH]136916[/ATTACH]

---

### Post by 3rdalbum on 2009-11-20
You've got swap, it just isn't being used because Linux just doesn't need to swap anything out. If you keep using your system a lot without rebooting, you might find that you get about 50 megabytes of swap use even though your memory isn't full.

---

### Post by Locutus_of_Borg on 2009-11-20
sudo gedit /etc/sysctl.conf

change the line that reads vm.swappiness=#

to a higher number to use more swap


you dont want to do this, though

---

### Post by alz3abi on 2009-11-20
yaah .. cuze i have 4 GB Ram .. swap no need when i keep restarting my ubuntu . 

thanks All

---

