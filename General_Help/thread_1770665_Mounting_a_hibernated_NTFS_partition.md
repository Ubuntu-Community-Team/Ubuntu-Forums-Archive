---
title: "Mounting a hibernated NTFS partition"
date: 2011-05-29
forum: General Help
---

### Post by hooah212002 on 2011-05-29
Hello all. I am running 11.4 from a thumb drive,mainly because something is fishy with my main hard drive, but installation is not my reason for this thread (though I think fixing one problem will remedy the other).

My winbloze install is short stroked with ~50gb for OS and ~200gb for media storage. I have no problem accessing the storage from windows, but I am unable to mount the storage partition under Ubuntu. I get the following error:

> Error mounting: mount exited with exit code 14: Hibernated non-system partition, refused to mount.
Failed to mount '/dev/sda2': Operation not permitted
The NTFS partition is hibernated. Please resume and shutdown Windows
properly, or mount the volume read-only with the 'ro' mount option, or
mount the volume read-write with the 'remove_hiberfile' mount option.
For example type on the command line:

            mount -t ntfs-3g -o remove_hiberfile /dev/sda2 /media/Laptop Storage

When I run that command, I get this:

> su: invalid option -- 't'

---

### Post by prodigy_ on 2011-05-29
> **hooah212002 said:**
> su: invalid option -- 't'
[Just use **sudo** command instead of **su**](https://help.ubuntu.com/community/RootSudo).

---

### Post by oldfred on 2011-05-29
Is your windows in hibernation? If so you will damage your windows install if you write into files or folders that the hibernation expects in one place and you have moved/deleted.

---

### Post by hooah212002 on 2011-05-29
> **oldfred said:**
> Is your windows in hibernation? If so you will damage your windows install if you write into files or folders that the hibernation expects in one place and you have moved/deleted.

My OS, no. I removed the option to even hibernate and never used the function. However, I do not recall whether or not I had it in hibernate prior to short stroking (if that's even possible or would make a difference).

---

### Post by hooah212002 on 2011-05-29
> **prodigy_ said:**
> [Just use **sudo** command instead of **su**]("https://help.ubuntu.com/community/RootSudo").

That gives me this:

> Usage: mount -V                 : print version
       mount -h                 : print this help
       mount                    : list mounted filesystems
       mount -l                 : idem, including volume labels
So far the informational part. Next the mounting.
The command is `mount [-t fstype] something somewhere'.
Details found in /etc/fstab may be omitted.
       mount -a [-t|-O] ...     : mount all stuff from /etc/fstab
       mount device             : mount device at the known place
       mount directory          : mount known device here
       mount -t type dev dir    : ordinary mount command
Note that one does not really mount a device, one mounts
a filesystem (of the given type) found on the device.
One can also mount an already visible directory tree elsewhere:
       mount --bind olddir newdir
or move a subtree:
       mount --move olddir newdir
One can change the type of mount containing the directory dir:
       mount --make-shared dir
       mount --make-slave dir
       mount --make-private dir
       mount --make-unbindable dir
One can change the type of all the mounts in a mount subtree
containing the directory dir:
       mount --make-rshared dir
       mount --make-rslave dir
       mount --make-rprivate dir
       mount --make-runbindable dir
A device can be given by name, say /dev/hda1 or /dev/cdrom,
or by label, using  -L label  or by uuid, using  -U uuid .
Other options: [-nfFrsvw] [-o options] [-p passwdfd].
For many more details, say  man 8 mount .which tells me the command is not correct. I wholeheartedly admit that my command-line-fu is severely lacking.

---

### Post by hooah212002 on 2011-05-29
Not certain what exactly I did, but in conjunction with NTFS Configuration Tool and the aforementioned command, I was able to mount the partition. Thank you all for your help. It's just too bad I don't know what exactly I did though.....

---

### Post by prodigy_ on 2011-05-29
> **hooah212002 said:**
> which tells me the command is not correct.
The simplest syntax to mount NTFS: ```
sudo mount -t ntfs /dev/<partition> /<path>/<to>/<mount_point>
```
Consult mount manpage (**man mount**) for more options.

---

