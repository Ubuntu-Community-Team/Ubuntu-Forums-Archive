---
title: "mount error(101): Network is unreachable"
date: 2010-05-06
forum: General Help
---

### Post by bowens44 on 2010-05-06
I am running Lucid 64bit. I have noticed that when booting I get the following errors when mounting cifs volumes during the boot process.


from boot.log:

mount error(101): Network is unreachable
Refer to the mount.cifs( 8 ) manual page (e.g. man mount.cifs)
mount error(101): Network is unreachable
Refer to the mount.cifs( 8 ) manual page (e.g. man mount.cifs)
mount error(101): Network is unreachable
Refer to the mount.cifs( 8 ) manual page (e.g. man mount.cifs)
mountall: mount /media/misc [932] terminated with status 32
mountall: mount /media/music [933] terminated with status 32
mountall: mount /media/fs_files [934] terminated with status 32

they do mount but this error pauses the boot process for 10 or 15 seconds. 

My assumption is that an attempt is made to mount the drives before the network is available.

Here's my fstab:

```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdc1 during installation
UUID=db3b4a6c-b264-409b-ba1a-46e540ae3697 /               ext3    errors=remount-ro 0       1
# /home was on /dev/sda3 during installation
UUID=88c8ed0c-43ee-4849-8fe3-a5603815c4d7 /home           ext3    defaults        0       2
# swap was on /dev/sdc5 during installation
UUID=32fb0558-2896-4532-86a2-480e33f08596 none            swap    sw              0       0

//192.168.5.102/misc /media/misc  cifs  credentials=/root/.smbcredentials,noperm,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0
//192.168.5.102/music /media/music  cifs  credentials=/root/.smbcredentials,noperm,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0
//192.168.5.102/files /media/fs_files  cifs  credentials=/root/.smbcredentials,noperm,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0

```


Any idea how to resolve this?

Thanks

---

### Post by dcstar on 2010-05-07
> **bowens44 said:**
> I am running Lucid 64bit. I have noticed that when booting I get the following errors when mounting cifs volumes during the boot process.
.......
My assumption is that an attempt is made to mount the drives before the network is available.

Here's my fstab:

```
# /etc/fstab: static file system information.
.........
//192.168.5.102/misc /media/misc  cifs  credentials=/root/.smbcredentials,noperm,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0
//192.168.5.102/music /media/music  cifs  credentials=/root/.smbcredentials,noperm,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0
//192.168.5.102/files /media/fs_files  cifs  credentials=/root/.smbcredentials,noperm,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0

```


Any idea how to resolve this?

Thanks

Use the **_netdev option**:
```

//192.168.5.102/misc /media/misc  cifs  credentials=/root/.smbcredentials,noperm,iocharset=utf8,file_mode=0777,dir_mode=0777,_netdev 0 0
//192.168.5.102/music /media/music  cifs  credentials=/root/.smbcredentials,noperm,iocharset=utf8,file_mode=0777,dir_mode=0777,_netdev 0 0
//192.168.5.102/files /media/fs_files  cifs  credentials=/root/.smbcredentials,noperm,iocharset=utf8,file_mode=0777,dir_mode=0777,_netdev 0 0
```

---

### Post by bowens44 on 2010-05-08
> **dcstar said:**
> Use the **_netdev option**:


Unfortunately, this made no difference

---

### Post by abqsteve on 2010-05-09
Worked for me.  On my system, WICD is now started, the wireless connection is made, and the shares are mounted.  Thank you for the help!

---

### Post by renardeau on 2011-01-03
I had this same problem after upgrading to Lucid and as I didn't find a solution, I used the /etc/rc.local script as workaround:
```

#!/bin/sh 
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.
mount -t cifs -o iocharset=utf8,user=myuser,password=mypwd,rw,uid=myuid,_netdev //server/share /mount/point

exit 0

```Hope this helps

---

### Post by adamjseed on 2011-10-13
Hi, 

I'd Like to revive this thread. 

I am getting the error described here even with the _netdev option under ubuntu 10.04

As renardeau said you can add these to the rc.local file which stops the error. 

My issue is that one of my mounts in my case is used for configs for vairous applications like SABNZBD + Sickbeard and using the rc.local method means that I cant use these applications as services. However the error(101) causes issuses with these applications on boot, as the mount is not available when the services are starting.

Does anyone have any more suggestions? I am thinking of trying a different version.

---

### Post by adamjseed on 2011-10-14
Ok so i have tried this on a few different versions now, 11.10  server and desktop. Both with the same issue. Its really strange. 

For me it means that I have to directly mount a native drive in order to use it as a 'Install disk'. Shame really

does anyone have any other ideas?

---

