---
title: "how to mount vmdk (vmware image) in linux"
date: 2006-04-03
forum: General Help
---

### Post by towsonu2003 on 2006-04-03
hostOS is Ubuntu
guestOS is Windows ( ;) )
the image that I wanna mount is .vmdk and formatted as fat32. I use it as the second (home) disk in vmware player (I don't have the vmware the real thing -too expensive).
This image used to be a qemu image (.raw) and I was able to easily mount it using: ```

/path/to/home.raw  /media/qemu  vfat rw,user,loop,noauto,offset=32256  0  0

```
I converted the image to vmdk using qemu-img convert, and it's working fine. But the same fstab line (adjusting /path/to/home.vmdk and /media/vmware) doesn't work with it. dmesg | tail says:
```

[4305889.981000] FAT: invalid media value (0x42)
[4305889.981000] VFS: Can't find a valid FAT filesystem on dev loop0.
```

How do you mount these vmdk images in linux? I know about networking (samba), but I would rather mount and unmount it.

---

### Post by patbuntu on 2006-04-04
Do you have a vmx file? If you don't create one.  Then start vmware player and choose it.

Mine looks like this (winxp.vmx in same directory as winxp.vmdk):

```

#!/usr/bin/vmware
config.version = "8"
virtualHW.version = "3"
memsize = "356"
ide0:0.present = "TRUE"
ide0:0.fileName = "/dev/hdd"
ide0:0.deviceType="atapi-cdrom"
ide1:0.present = "TRUE"
ide1:0.fileName = "winxp.vmdk"

ethernet0.present = "TRUE"
ethernet0.connectionType = "nat"
usb.present = "TRUE"
sound.present = "TRUE"
sound.virtualDev = "es1371"
displayName = "Windows XP Home"
guestOS = "ubuntu"
nvram = "ubuntu.nvram"
scsi0:0.redo = ""
ethernet0.addressType = "generated"
uuid.location = "56 4d 6c 8f 3c 8c 6a fb-86 db 48 e7 3a c8 10 a5"
uuid.bios = "56 4d 6c 8f 3c 8c 6a fb-86 db 48 e7 3a c8 10 a5"
ide1:0.autodetect = "TRUE"
ethernet0.generatedAddress = "00:0c:29:c8:10:a5"
ethernet0.generatedAddressOffset = "0"
checkpoint.vmState = ""
tools.remindInstall = "TRUE"
ide0:0.redo = ""

ide1:0.redo = ""

usb.autoConnect.device0 = ""

```

Not sure if you can mount it directly though.

Hope this helps

-Pat

---

### Post by towsonu2003 on 2006-04-05
the problem isn't with booting from vmware though. I wanna mount the windows.vmdk file as a partition/disk using "sudo mount" (or fstab) when vmdk isn't in use. 

in qemu, that's very easy bc the info is available (which I have posted in my fstab output above), but there was no info for mounting a vmdk file as a partition/disk. [without using samba]

---

### Post by towsonu2003 on 2006-04-05
bump

---

### Post by GermanyZulu on 2006-12-24
I found the answer here: [http://http://www.vmware.com/community/thread.jspa?messageID=445208]("http://http://www.vmware.com/community/thread.jspa?messageID=445208")

This command you want is ```
vmware-mount.pl
``` It is installed along with vmware (server is all I have installed dont know about other versions)

Run it all by itself to see the necessary options:
```

This script requires 3 (not 0) mandatory argument(s).

Usage: /usr/bin/vmware-mount.pl
        -p          : Print the partition table
        disk        : Name of the Virtual Hard Disk file
or
        disk        : Name of the Virtual Hard Disk file
        partition   : Number of the partition
        [-t type]   : Partition type
        [-o options]: Partition mount options(s)
        mount-point : Directory where to mount the partition
```

For example you could do:


```

GZ@GZ:~$ cd /var/vmware/ReactOS/
GZ@GZ:/var/vmware/ReactOS$ ls
nvram              ReactOS-s002.vmdk  ReactOS.vmsd  vmware-0.log  vmware-2.log
ReactOS-s001.vmdk  ReactOS.vmdk       ReactOS.vmx   vmware-1.log  vmware.log

GZ@GZ:/var/vmware/ReactOS$ mkdir mount.point
GZ@GZ:/var/vmware/ReactOS$ sudo vmware-mount.pl ./ReactOS.vmdk 1 ./mount.point.dir/
Password:

--------------------------------------------
VMware for Linux - Virtual Hard Disk Mounter
Version: 1.0 build-29996
Copyright 1998 VMware, Inc.  All rights reserved. -- VMware Confidential
--------------------------------------------

It has been reported that this program does not work correctly with 2.4+ Linux
kernels in some cases, and you are currently running such a kernel. Do you
really want to continue? [N] y

No Network Block Device detected.

There is no Network Block Device defined on this machine. This script is about
to create the /dev/nb0 Network Block Device. Continue? [Y]

Creating the /dev/nb0 Network Block Device

No Network Block Device driver detected.

Trying to load the Network Block Device driver kernel module... Success.

Client: The partition is now mapped on the /dev/nb0 Network Block Device.

Using another terminal, you can now browse your Virtual Hard Disk partition in
./mount.point/. Hit Control-C in this terminal when done.

```

Please note: I am running a custom 2.6.17.3 Kernel and still get the question about a 2.4 Kernel.  Also the 3 mandatory options are: "Disk", "Partition", and "Mount Point" ;) 

--GZ

---

### Post by towsonu2003 on 2006-12-25
great help, thanks a lot :)

---

### Post by flaggh on 2007-10-31
Has anybody tried this method to clone or resize vmware images?  

I figure the steps involved would be something like this:

1.  Create new vmware image with desired size and settings.
2.  Mount existing vmware image that you wish to clone.
3.  Mount new vmware image.
4.  Copy all files from existing vmware image to new vmware image.

Would this create a bootable partition?

---

