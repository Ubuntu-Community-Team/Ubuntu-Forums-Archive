---
title: "Windows partition automount as /mount/OS, how to disable?"
date: 2009-11-18
forum: General Help
---

### Post by kotelyan on 2009-11-18
I have Ubuntu 9.04 running as a dual-boot  with Vista, and it automatically mounts Windows partition at boot. It's nice, but I noticed that ANY user can read/write/delete any files there. How can I disable it from auto- mounting, but still keep an 'OS" icon to appear in the File Browser, so tha it can be mounted, when needed?

---

### Post by klemes on 2009-11-18
Look for the corresponding entry in fstab (the one containing /mount/OS as the mount point and comment it out.
As for the other I dont know because I am currently using Kubuntu.
Maybe someone that uses Ubuntu will answer this .

---

### Post by fluffman86 on 2009-11-18
Klemes is right.  Removing it from fstab ("gksu gedit /etc/fstab" after pressing alt+f2) will make it not automount, and it will still appear under Places and in Nautilus, but will require an Admin password.  You may also want to take a look at System > Administration > Users and Groups, then use Properties to adjust the user privileges to make sure that people can't automatically mount external filesystems.

---

### Post by Aubergines on 2009-11-18
Hmm I didn't think it'll auto mount the windows partition automatically. Then again I run my windows and linux on seperate drives - maybe it makes a difference. But any way inside your /etc/fstab file you'll see an entry for your windows partition. Giving it a mount point option of "noauto" will stop it from auto mounting. You can also give it "nouser" which will prevent anyone who isn't root user from mounting it.

Check this for more details - [http://www.tuxfiles.org/linuxhelp/fstab.html](http://www.tuxfiles.org/linuxhelp/fstab.html)

---

### Post by kotelyan on 2009-11-18
> **Aubergines said:**
> Hmm I didn't think it'll auto mount the windows partition automatically. Then again I run my windows and linux on seperate drives - maybe it makes a difference. But any way inside your /etc/fstab file you'll see an entry for your windows partition. Giving it a mount point option of "noauto" will stop it from auto mounting. You can also give it "nouser" which will prevent anyone who isn't root user from mounting it.

Check this for more details - [http://www.tuxfiles.org/linuxhelp/fstab.html](http://www.tuxfiles.org/linuxhelp/fstab.html)
Aha, but that's the mystery - it does NOT show in the /etc/fstab.  ????

when it's mounted it's partition /dev/sda3/ mounted as  /mount/OS 
see below:
----->
kotelyan@MK-laptop:~$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda6            104467516  14987112  84173740  16% /
tmpfs                  1981204         0   1981204   0% /lib/init/rw
varrun                 1981204       348   1980856   1% /var/run
varlock                1981204         0   1981204   0% /var/lock
udev                   1981204       172   1981032   1% /dev
tmpfs                  1981204       996   1980208   1% /dev/shm
lrm                    1981204      2560   1978644   1% /lib/modules/2.6.28-16-generic/volatile
none                   1981204       796   1980408   1% /tmp/guest-home.vpMZnN
/dev/sda3            112631708  57428792  55202916  51% /media/OS
------------------------------------>

BUT it is not mentioned in the /etc/fstab ...????




----------------------------------------------------------------------------------------------------------->
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda6 during installation
UUID=8ccb9056-64a0-423d-bd17-ec20a7b0f108 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=57d47b4f-a542-4918-ace3-4b8a180dc9b4 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
-------------------------------------------------------------------------------------------------------------------->

---

### Post by Aubergines on 2009-11-18
Damn Gnome! :P Try typing the following command
```
gconf-editor /apps/nautilus/desktop
```
Then untick "volumes_visible".

---

### Post by drumond.douglas on 2010-07-13
```
sudo gedit /var/lib/polkit-1/localauthority/10-vendor.d/com.ubuntu.desktop.pkla
```

In the first section, [Mounting, checking, etc. of internal drives], change ResultActive=yes to ResultActive=auth_admin_keep

---

