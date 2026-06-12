---
title: "Can't set permissions on RAID mount"
date: 2009-11-03
forum: General Help
---

### Post by xynamax on 2009-11-03
I'm having trouble setting permissions on a RAID mount that I created with mdadm.

My goal is to create a RAID-1 array and mount it to the path /backup/alt and give all users read-write-execute permissions to the device.

The RAID array in question is RAID-1 created with the command

```
mdadm --create /dev/md0 --level=1 --raid-devices=2 /dev/sdb1 /dev/sdc1
```

The command executed successfully and the array is currently resynching and at about 30%

I mounted the new array /dev/md0 to /backup/alt with the command

```
mount /dev/md0 /backup/alt
```
which executed successfully

While waiting for this epic resync I decided to test the permissions by copying a file to the newly mounted device.  This is where I ran into trouble.

As root I was able to copy files to and from anywhere on my system to /backup/alt  however as the standard user ($ prompt) I just get "permission denied" errors when attempting to copy files to the folder /backup/alt.

I checked the permissions on the folder /backup/alt and they are

```
drwxr-xr-x
```

so I attempted to give write permissions with 

```
chmod 777 /backup/alt
```

The command appears to execute successfully but when I check the permissions  it still reads the same as before.  I've also tried unmounting the device, chmodding the mount point, and remounting the device and the permissions instantly revert to drwxr-xr-x when i mount it.

Is this something to do with the fact the array is still resyncing or do I need to do something else?

TIA.

---

### Post by xynamax on 2009-11-04
Can anyone offer me any advice please?

did I post this in the wrong forum?

---

### Post by xynamax on 2009-11-04
Problem solved! it was the mount settings.

I needed to mount the device with the -t flag as 'vfat' and specify 'umask=000 0 0'

the fstab line looks like

```
/dev/md0 /backup/foo vfat defaults,umask=000 0 0
```

hope this helps anyone in the same situation.):P

---

