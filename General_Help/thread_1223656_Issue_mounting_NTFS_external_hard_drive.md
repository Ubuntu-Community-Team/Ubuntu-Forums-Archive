---
title: "Issue mounting NTFS external hard drive"
date: 2009-07-26
forum: General Help
---

### Post by beastrace91 on 2009-07-26
Hey,

So recently a friends external hard drive on Ubuntu started getting an "Unable to mount" error when it was connected. When I connect it to my laptop it auto mounts the device just fine... Here is the terminal out put from manually trying to mount the device: ```
root@grizz:/media# mount -t ntfs /dev/sdb /mnt/disk
NTFS signature is missing.
Failed to mount '/dev/sdb': Invalid argument
The device '/dev/sdb' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?

```

Any ideas?
~Jeff

---

### Post by beastrace91 on 2009-07-26
After talking to my friend some more he informed me that he had right clicked on the hard drive, selected properties, clicked into the volume tab and then gone into "settings", where he added an unmount command to the mount line... Goofy I know. Anywho is there a way I can clear the settings for this device on his computer?

Thanks,
~Jeff

---

