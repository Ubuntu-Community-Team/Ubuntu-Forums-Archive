---
title: "How do I mount my Time Machine drive in Ubuntu 9.10?"
date: 2010-03-21
forum: General Help
---

### Post by jona26 on 2010-03-21
Please help: 

I have a Time Machine back up of my old macbook that was stolen.

I have installed hfsplus and libhfsp0 via synaptic. 

When I ran: 'cat /boot/config-2.6.31-20-generic | grep HFS' in the terminal...

I got:
CONFIG_NET_SCH_HFSC=m
CONFIG_HFS_FS=m
CONFIG_HFSPLUS_FS=m
CONFIG_SQUASHFS=m
# CONFIG_SQUASHFS_EMBEDDED is not set
CONFIG_SQUASHFS_FRAGMENT_CACHE_SIZE=3

I read in some other post that any line starting with '#' needed to end with '=m'

I'm a total newb to Linux from mac, and I'm enjoying it. I'd just like to be able to mount my time machine drive. 

Also, when I run lsmod, hfsplus is in my modules. 

Any help is appreciated.

Thanks!

---

### Post by soltanis on 2010-03-21
You're going to need to mount your Time Machine drive. When you plug it in, does it mount itself automatically (an icon typically appears on your desktop)?

If not, you will need to mount it automatically. You need to determine which dev node the drive is located at, then run

```

sudo mkdir /media/tm
sudo mount -t hfsplus /dev/<tm_drive> /media/tm

```

To try to find out what device node the device is at, plug it in, and it should show up under "Computer" in the file browser. Right-clicking and hitting "Properties" should inform you of the correct drive device node.

---

### Post by jona26 on 2010-03-21
Soltanis, 

Thanks for your help. When I plug it in, the drive is receiving power from the USB port but it isn't even recognized in the 'Computer' folder. It's definitely not a problem with the USB port because it recognizes a flash drive that I plug into it...

I'd love to follow your steps but I can't even get the OS to recognize that the external drive is connected... Any ideas?

---

### Post by adamlogan on 2010-06-18
I'm struggling with the same thing. Although I'm speaking of Ubuntu 10.4 LTS. I checked LSMOD and saw HFSPLUS in there. I chmodded everything on the drobo to 777 on the mac before plugging the drobo into my ibm w/ ubuntu. I can see the drobo in the computer, but if I look at properties it is basically empty. However if I try and open it or mount it it says unable to mount location, "Error mounting: mount: wrong fs type, bad option, bad superblock on /dev/sdb1, misssing codepage or helper program, or other error In some cases useful info is found in syslog - try dmesg | tail or so.

Trying "dmesg | tail" relevant output states that "volumes larger than 2tb are not supported yet", & "unable to find HFS+ superblock".

I did try mounting /dev/sdb1/ per your instructions Soltanis but no go.. Also tried the fstab route, nothing there either.

---

