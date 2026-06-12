---
title: "Automount USB stick to same mount point, always"
date: 2009-09-23
forum: General Help
---

### Post by beow on 2009-09-23
I have a 16G USB stick permanently installed in my desktop for doing nightly backups. The backup program (backintime) relies on that it is mounted on 

/media/disk

However, when I restart the computer it mounts (automatically, no fstab entry) as 

/media/disk-1

instead. There is a also a mount point /media/disk but it is not used. Any suggestions on having it automatically mounted to /media/disk every time? (I know I could change backintime to use /media/disk-1 instead but I'm not certain the USB stick would always mount to that point).

BR

---

### Post by StuartN on 2009-09-23
> **beow said:**
> However, when I restart the computer it mounts (automatically, no fstab entry) as /media/disk-1

I think it mounts as <name>-1 because there is already a folder called <name>. You can give your USB stick a unique name by changing the partition label using mtools, e.g. to call it "my_external":

```
sudo apt-get install mtools
sudo mlabel -i /dev/sdb1 ::my_external
```
(see [https://help.ubuntu.com/community/RenameUSBDrive](https://help.ubuntu.com/community/RenameUSBDrive)).

Once it has a unique partition label, the USB drive will automount to a folder in /media with that name, which should not exist beforehand.

---

### Post by beow on 2009-09-24
> I think it mounts as <name>-1 because there is already a folder called <name>

Yes that was it. I unmounted "disk-1" and the removed the folder "disk" and then mounted it again, know to "disk". So I think it will mount to that name from now on.

Thanks.

---

### Post by michy99 on 2009-09-24
Just be aware that if the backup program runs without the usb stick being mounted, it will create a new directory called 'disk' and backup to it. The next time you mount the stick, it will be back to 'disk-1' again.

---

### Post by dcstar on 2009-09-25
> **michy99 said:**
> Just be aware that if the backup program runs without the usb stick being mounted, it will create a new directory called 'disk' and backup to it. The next time you mount the stick, it will be back to 'disk-1' again.

Which is why any automated backup to removable media needs to check if the media actually exists before it proceeds.

---

