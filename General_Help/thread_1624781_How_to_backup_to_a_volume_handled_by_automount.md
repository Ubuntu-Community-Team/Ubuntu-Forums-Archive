---
title: "How to backup to a volume handled by automount?"
date: 2010-11-18
forum: General Help
---

### Post by frafu on 2010-11-18
Hello, 

I am using a script that is invoked by cron to backup a volume (let's call it srcVol) to another volume (let's call it backupVol) by using rsync. Until now, both volumes were mounted by fstab. 

Now, I would like to remove the backupVol from fstab and have it automatically mount by the backup script.

I am aware that I can create a mountpoint at the start of the backup script, mount the volume on it, make the backups, unmount the volume and delete the mountpoint afterwards.

However, I wonder whether there is not a simpler way to achieve this by using the autofs/automount facility of Ubuntu, that for example automatically mounts a volume by clicking on its label in the sidebar of nautilus.

Thanks in advance for any reply. 

Cheers, 

Francesco.

---

### Post by dcstar on 2010-11-18
> **frafu said:**
> Hello, 

I am using a script that is invoked by cron to backup a volume (let's call it srcVol) to another volume (let's call it backupVol) by using rsync. Until now, both volumes were mounted by fstab. 

Now, I would like to remove the backupVol from fstab and have it automatically mount by the backup script.
.........

Leave it in /etc/fstab and use the **noauto** option. You will then be able to mount it with a specific mount command and unmount it in the same way.

---

### Post by frafu on 2010-12-03
> **dcstar said:**
> Leave it in /etc/fstab and use the **noauto** option. You will then be able to mount it with a specific mount command and unmount it in the same way.

Hi dcstar, 

First off all, thanks for your reply and sorry for getting back to you so late. 

I tried your suggestion about adding noauto to the corresponding line in fstab; but I got error messages when trying to mount/unmount it from user space. I suppose that root privileges are required to mount and unmount a volume if it is listed in fstab. 

For those interested, here is how I got it to work:

- I added the following line at the bottom of /etc/auto.master
```

/media/Local    /etc/auto.pers  --ghost

```

I had to tell autofs to use a subdirectory (I choose to call it 'Local' as I mount a local disk into it) of /media; I first tried to make autofs mount the content of auto.pers directly in /media, but that disturbed the mounting of other devices in /media. 

- I created the /etc/auto.pers file with the following content, and with 644 (rw-r--r--) as permissions
```

#
# This is the /etc/auto.pers file.
#
backupVol   -fstype=auto  :/dev/disk/by-uuid/uuid_of_the_volume

```

Of course, you have to replace 'uuid_of_the_volume' with the real uuid of the volume. You can get the uuid by using the 'gnome-device-manager' application. It probably also works with the ':/dev/sdXY' notation for the volume to mount.

Finally, I had autofs already running for other mounts on my system and cannot tell now from the top of my head whether there are additional steps required to enable autofs.

Cheers, 

Francesco.

---

### Post by frafu on 2011-02-17
> **frafu said:**
> 

I tried your suggestion about adding noauto to the corresponding line in fstab; but I got error messages when trying to mount/unmount it from user space. I suppose that root privileges are required to mount and unmount a volume if it is listed in fstab. 




In the meantime, I know why using the keyword "noauto" in the fstab line did not work: I tried to mount it with the usual command line. Instead it has to be mounted the following way: 

```

mount /path/to/mountpoint

```

I suppose it is that way, because it knows from the fstab what to mount at the mountpoint. 

Moreover, if I got it right, the keyword "users" has to be added to the options of the mount in order to allow any user to mount the volume. By adding the keyword "user" (instead of users) only the owner will be able to mount it.

As I am not very familiar with this topic, please use these explanations only as starting point for where to look if you are confronted to a similar problem. 

Cheers, 

Francesco.

---

