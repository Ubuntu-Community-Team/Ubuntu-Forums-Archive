---
title: "Ubuntu startup failure"
date: 2011-03-28
forum: General Help
---

### Post by Darkchef on 2011-03-28
Hello,

My Ubuntu 10.10 installation has recently stopped working and it appears to be due to some mounting errors although this installation has been working for years which suggests that it may be due to corruption.

I am presented with these errors after selecting Ubuntu from the GRUB menu during bootup:

```

Killed
mount: mounting /dev on /root/dev failed: No such file or directory
mount: mounting /sys on /root/sys failed: No such file or directory
mount: mounting /proc on /root/proc failed: No such file or directory
Target filesystem doesn't have requested /sbin/init
No init found. Try passing init= bootarg.

```

I am then presented with a terminal called BusyBox which appears to be a severely limited version of bash.

Is there any way of recovering this installation by using the Ubuntu 10.10 live CD?

Thanks.

---

### Post by sikander3786 on 2011-03-28
I would first try running fsck from the Live CD.

```
sudo e2fsck -C0 -p -f -v /dev/sda5
```

Replace sda5 with your intended partition.

If there are errors, try this one.

```
sudo e2fsck -f -y -v /dev/sda5
```

Let us know how that goes or we might need to see the output of [bootinfoscript]("http://bootinfoscript.sourceforge.net").

---

### Post by Darkchef on 2011-03-28
> **sikander3786 said:**
> I would first try running fsck from the Live CD.

```
sudo e2fsck -C0 -p -f -v /dev/sda5
```

Replace sda5 with your intended partition.

If there are errors, try this one.

```
sudo e2fsck -f -y -v /dev/sda5
```

Let us know how that goes or we might need to see the output of [bootinfoscript]("http://bootinfoscript.sourceforge.net").

Thanks for the quick reply, I've tried to use the commands you have given but it says that /dev/sda5 is being locked by a specific program. Not sure how to get round this. Any ideas?

---

### Post by sikander3786 on 2011-03-28
Are you sure sda5 is your Ubuntu partition? If unsure, please post the output of this command.

```
sudo fdisk -l
```

And for lock errors, we need to see the exact error message. Please paste it in your post.

---

### Post by Darkchef on 2011-03-28
> **sikander3786 said:**
> Are you sure sda5 is your Ubuntu partition? If unsure, please post the output of this command.

```
sudo fdisk -l
```

And for lock errors, we need to see the exact error message. Please paste it in your post.

Ok I believe that the ubuntu installation is in sda5, here is the output of the command you gave me:

```

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x344c344b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        8289    66581361    7  HPFS/NTFS
/dev/sda2            8290       14593    50636880    5  Extended
/dev/sda5            8290       14330    48524301   83  Linux
/dev/sda6           14331       14593     2112516   82  Linux swap / Solaris

Disk /dev/mmcblk0: 1015 MB, 1015808000 bytes
32 heads, 63 sectors/track, 984 cylinders
Units = cylinders of 2016 * 512 = 1032192 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

        Device Boot      Start         End      Blocks   Id  System
/dev/mmcblk0p1               1         984      991747+   6  FAT16

```

It must be /dev/sda5 ?

EDIT: The lock error i've been getting from using :

```

sudo e2fsck -C0 -p -f -v /dev/sda5

```

Is:

```

e2fsck: Device or resource busy while trying to open /dev/sda5
Filesystem mounted or opened exclusively by another program?

```

---

### Post by sikander3786 on 2011-03-29
Yes your Ubuntu partition is sda5.

The errors don't look good at all. I suspect your HDD is failing.

Fire up Disk Manager from System > Administration menu and click 'View Smart Data'. Does it list any errors or failures?

Or you can alternatively download the manufacturer's diagnostic tools from their official website and scan your disk.

---

### Post by Darkchef on 2011-03-29
> **sikander3786 said:**
> Yes your Ubuntu partition is sda5.

The errors don't look good at all. I suspect your HDD is failing.

Fire up Disk Manager from System > Administration menu and click 'View Smart Data'. Does it list any errors or failures?

Or you can alternatively download the manufacturer's diagnostic tools from their official website and scan your disk.

Yeah it wouldn't show any SMART data as it says its unsupported. I did do a check on /dev/sda5 and it says the filesystem is unclean, is there any way of recovering any data from the partition?

---

### Post by Darkchef on 2011-03-29
> **sikander3786 said:**
> Yes your Ubuntu partition is sda5.

The errors don't look good at all. I suspect your HDD is failing.

Fire up Disk Manager from System > Administration menu and click 'View Smart Data'. Does it list any errors or failures?

Or you can alternatively download the manufacturer's diagnostic tools from their official website and scan your disk.

I'm going to see if testdisk will be able to repair the partition, will post results...

---

### Post by Darkchef on 2011-03-29
> **Darkchef said:**
> I'm going to see if testdisk will be able to repair the partition, will post results...

No luck so far, I guess I just need to accept that its lost, I had a file or two on there that I needed .... :confused:

---

### Post by sikander3786 on 2011-03-30
> **Darkchef said:**
> No luck so far, I guess I just need to accept that its lost, I had a file or two on there that I needed .... :confused:
Apologies for the late reply. I was offline for a couple of days and no-one else jumped in either...

So what happened with testdisk? How far did you get?

Did you try this?

[http://ubuntu4beginners.blogspot.com/2011/01/recover-deleted-data-using-photorec-in.html](http://ubuntu4beginners.blogspot.com/2011/01/recover-deleted-data-using-photorec-in.html)

---

### Post by matt_symes on 2011-03-30
Hi

What does (From a LiveCD)....

```
sudo file -sL /dev/sda5
```

return. As Sikander said what issues were you having with testdisk ?

Post back.

Kind regards

---

### Post by Darkchef on 2011-03-30
> **sikander3786 said:**
> Apologies for the late reply. I was offline for a couple of days and no-one else jumped in either...

So what happened with testdisk? How far did you get?

Did you try this?

[http://ubuntu4beginners.blogspot.com/2011/01/recover-deleted-data-using-photorec-in.html](http://ubuntu4beginners.blogspot.com/2011/01/recover-deleted-data-using-photorec-in.html)

Hello, thanks for the reply. Yeah not much help from people with this. Thanks I will try out this photorec app, hopefully it can recover the data.

Well i ran testdisk ok, but i dont think I was using it correctly. It didnt seem to be finding problems like I expected. I may have been using it incorrectly. I need to look into it a bit more.

---

### Post by Darkchef on 2011-03-30
> **matt_symes said:**
> Hi

What does (From a LiveCD)....

```
sudo file -sL /dev/sda5
```

return. As Sikander said what issues were you having with testdisk ?

Post back.

Kind regards

I have just retried testdisk app and then tried to boot ubuntu and it come up with a message saying it was trying to fix the partition problem and now it is working fine. Thanks for the help anyway!

---

