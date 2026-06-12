---
title: "impossible to unmount ntfs disk"
date: 2011-06-27
forum: General Help
---

### Post by Gingalone on 2011-06-27
I have just bought a WD USB disk and (of course) it is formatted in NTFS and I want to reformat it to ext3.
But Gparted can't unmount it, I get the info:

[INDENT]Unable to find mount point
Unable to read the contents of this file system!
Because of this some operations may be unavailable.

The following list of software packages is required for ntfs
file system support: ntfsprogrs.
[/INDENT]
But ntfsprogrs is already installed on my Ubuntu (Natty) system!

What about? :confused: How can I reformat that disk?

Thanks for help.

---

### Post by Gingalone on 2011-06-27
I forgot: the fs of the usb disk is seen as fuseblk by the system monitor.

---

### Post by blueridgedog on 2011-06-27
With the disk plugged in, what is the output of 

```
sudo fdisk -l
```

and 

```
mount
```

---

### Post by seawolf167 on 2011-06-27
Just to be sure, you have 

```
sudo apt-get install ntfsprogs
```

installed, and running gparted as root

```
gksu gparted
```

doesn't allow you to format the disk?

---

### Post by Gingalone on 2011-06-27
Thanks to seawolf167 & blueridgedog!

I was able to format it to ext3 after umount (right click in computer:///  window) and running Gparted afterwards.
Now two more strange things:

1) even if the disk is totally empty (just formatted) Nautilus tells me there are 35 GB (out of 750) used in the disk.

2) when I unmount the disk if I am not quick to remove it, it is "automatically" remounted in a few seconds...

Has USB3 (disk is compliant) something to do with that strange behaviour?

---

### Post by seawolf167 on 2011-06-27
> **Gingalone said:**
> 
1) even if the disk is totally empty (just formatted) Nautilus tells me there are 35 GB (out of 750) used in the disk.

ext3 reserves 5% for root


> **Gingalone said:**
> 
2) when I unmount the disk if I am not quick to remove it, it is "automatically" remounted in a few seconds...

Has USB3 (disk is compliant) something to do with that strange behaviour?

Not sure about this. Did you give this drive an /etc/fstab entry?

---

### Post by coffeecat on 2011-06-27
> **Gingalone said:**
> 
2) when I unmount the disk if I am not quick to remove it, it is "automatically" remounted in a few seconds...

Does the USB controller in your machine have a nvidia chipset? If you are not sure, run this from a terminal:

```
lspci | grep -i usb
```

If you have a nvidia USB controller, you have been hit with this bug:

[https://bugs.launchpad.net/ubuntu/+source/udev/+bug/624755](https://bugs.launchpad.net/ubuntu/+source/udev/+bug/624755)

Duplicate here:

[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/792085](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/792085)

But only in the first has the nvidia controller been identified as the problem. Also, the title of the first is misleading. If you choose "eject" with a pendrive, this does not occur. But with USB hard drives, you only get the "safely remove" option.

---

### Post by Gingalone on 2011-06-27
> Originally Posted by Gingalone 
2) when I unmount the disk if I am not quick to remove it, it is "automatically" remounted in a few seconds...

Not sure about this. Did you give this drive an /etc/fstab entry?

I didn't

> Posted by coffeecat:
Does the USB controller in your machine have a nvidia chipset?

usb controllers chipsets are Intel

---

