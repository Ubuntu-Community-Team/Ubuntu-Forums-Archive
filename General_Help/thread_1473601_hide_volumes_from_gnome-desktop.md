---
title: "hide volumes from gnome-desktop"
date: 2010-05-05
forum: General Help
---

### Post by side on 2010-05-05
Goodmorning,
Before anything I just want to apologize for my awful english (french people just talk/write french, that's a fact :p )

So, I have troubles with gnome menu volumes. I just want to hide them from the netbook-laucher but anything I've tried worked.
I have two Windows / NTFS partitions wich are readeable/writable 
in ubuntu Lucid Lynx Netbook Remix. One is the C: partition, the other is the boot partition from Windows 7.
This computer is for a public place so I can't let them just visible.

To hide them I try few things :

```
ls -lR /dev/disk
```

```
/dev/disk/by-label:
total 0
lrwxrwxrwx 1 root root 10 2010-05-05 09:59 Acer -> ../../sda3
lrwxrwxrwx 1 root root 10 2010-05-05 09:59 PQSERVICE -> ../../sda1
lrwxrwxrwx 1 root root 10 2010-05-05 10:05 SYSTEM\x20RESERVED -> ../../sda2
```

Visible volumes are Acer and SYSTEM RESERVED. Curiously PQSERVICE is not appering.

That's what I try :

```
sudo nano /usr/share/hal/fdi/preprobe/95userpolicy/10ignore-disks.fdi
```

Witth that in it :

```
<?xml version="1.0" encoding="UTF-8"?>
<deviceinfo version="0.2">
<device>
<match key="block.device" string="/dev/sda2">
<merge key="info.ignore" type="bool">true</merge>
</match>
</device>
<device>
<match key="block.device" string="/dev/sda3">
<merge key="info.ignore" type="bool">true</merge>
</match>
</device>
</deviceinfo>
```

Didn't work.

Then,

```
sudo nano /etc/udev/rules.d/95-hide-partitions.rules
```

```
# we only care about block devices
ACTION!="add|change", GOTO="hide_partitions_end"
SUBSYSTEM!="block", GOTO="hide_partitions_end"
KERNEL=="loop*|ram*", GOTO="hide_partitions_end"

################################################## ############################

# Partitions which desktops should not display
KERNEL=="sda2", ENV{DKD_PRESENTATION_HIDE}="1"
KERNEL=="sda3", ENV{DKD_PRESENTATION_HIDE}="1"
################################################## ############################

LABEL="hide_partitions_end"
```

Didn't work.

So I decided to declare the partition in /etc/fstab like this :

```
sudo nano /etc/fstab
```

```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=1fe12b6b-06a4-47fd-ae5f-99ffa76cd6c5 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda8 during installation
UUID=9a0fdda8-0cc6-49a3-9e57-8b9c7f6197a8 /home           ext4    defaults        0       2
# /media/DATA was on /dev/sda5 during installation
UUID=682242787C3D61AD /media/DATA     ntfs    defaults,auto,nls=utf8,umask=007,gid=46 0       0
# swap was on /dev/sda7 during installation
UUID=9f719c9c-754f-43b4-89db-b504fc3200cb none            swap    sw              0       0
# SYSTEM RESERVED (partition demarrage Windows 7) /dev/sda2
UUID=148AAF8E8AAF6AC6   /mnt/windows_boot       ntfs    ro,noauto,nouser,nls=utf8,umask=0222,gid=46 0       0
# Acer (partition C:) /dev/sda3
UUID=4E5EB1195EB0FAB3 /mnt/windows      ntfs    ro,noauto,nouser,nls=utf8,umask=0222,gid=46 0       0
```

Result : Acer volume disapear but not SYSTEM RESERVED !! :-x

So I move 95-hide-partitions.rules 

```
sudo mv /etc/udev/rules.d/95-hide-partitions.rules /lib/udev/rules.d/
```

But nothings change.

I try to add some line in it

```
# we only care about block devices
ACTION!="add|change", GOTO="hide_partitions_end"
SUBSYSTEM!="block", GOTO="hide_partitions_end"
KERNEL=="loop*|ram*", GOTO="hide_partitions_end"

##############################################################################

# Partitions which desktops should not display
KERNEL=="sda3", ENV{DKD_PRESENTATION_HIDE}="1"
KERNEL=="sda2", ENV{DKD_PRESENTATION_HIDE}="1"

# recovery partitions (taken from old hal rules)
ENV{ID_FS_TYPE}=="ntfs|vfat", \
  ENV{ID_FS_LABEL}=="RECOVERY|SYSTEM\x20RESERVED|SYSTEM RESERVED|HP_RECOVERY|Recovery Partition|DellUtility|DellRestore|IBM_SERVICE|SERVICEV001|SERVICEV002", \
  ENV{UDISKS_PRESENTATION_HIDE}="1"
##############################################################################

LABEL="hide_partitions_end"
```
Hope this could tell the system that SYSTEM RESERVED is a restauration volume, so don't show it ... but it failed.

I also use the gconf-editor /apps --> nautilus --> desktop. Uncheck volumes_visible. (Edit : this effectively worked on gnome-desktop, I should use /apps/netbook-launcher/volume_exclude_list but this is not working at all).

Just nothing work. SYSTEM RESERVED is still visible readeable/writable, the only change I notice is that regarding the changes I made, it's mount itself automaticaly at boot or not. When I change rights on the partition manually, it's removed after reboot.

I don't know what to do anymore, so I asking help here with my approximative english.

Thanks for all.

---

### Post by scouser73 on 2010-05-05
To not have the volumes show on the desktop, please follow these instructions.

**1** - Press **Alt & F2**

**2** - Type **gconf-editor**

**3** - Click on **Apps** & then scroll to **Nautilus**

**4** - Press the **+** sign at the side of Nautilus

**5** - Select **Desktop** & untick **volumes_visible**

Now you won't have any volumes on the desktop.

---

### Post by side on 2010-05-05
> **scouser73 said:**
> To not have the volumes show on the desktop, please follow these instructions.

**1** - Press **Alt & F2**

**2** - Type **gconf-editor**

**3** - Click on **Apps** & then scroll to **Nautilus**

**4** - Press the **+** sign at the side of Nautilus

**5** - Select **Desktop** & untick **volumes_visible**

Now you won't have any volumes on the desktop.

I have allready made that. 
> I also use the gconf-editor /apps --> nautilus --> desktop. Uncheck volumes_visible.
It did'nt work for me.

Edit : Probably because I use Netbook Remix. I have to edit /apps/netbook-launcher/volume_exclude_list in the gconf editor. God damn, it does not work at all !

---

### Post by jarreboum on 2010-05-06
There was that solution, but it seems it does not work anymore.

[http://www.martinhenze.de/2007/05/27/hide-unmounted-volumes-in-nautilus/](http://www.martinhenze.de/2007/05/27/hide-unmounted-volumes-in-nautilus/)

btw you don't want to hide volums from gnome-desktop, but from netbook-launcher

---

### Post by side on 2010-05-07
> **jarreboum said:**
> There was that solution, but it seems it does not work anymore.

[http://www.martinhenze.de/2007/05/27/hide-unmounted-volumes-in-nautilus/](http://www.martinhenze.de/2007/05/27/hide-unmounted-volumes-in-nautilus/)

Yes, I try this. It's not working.

> **jarreboum said:**
> btw you don't want to hide volums from gnome-desktop, but from netbook-launcher

Right. I edit my first post ...

---

