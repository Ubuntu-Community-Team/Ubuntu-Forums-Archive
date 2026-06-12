---
title: "repeated checksum issue, HDD backup w/ DD over USB"
date: 2010-10-01
forum: General Help
---

### Post by sippyCUP on 2010-10-01
Howdy,

Using Ubuntu 10.04 on an old HP DV4000 laptop. Trying to do a backup from my laptop's disk to an external USB drive using DD while booted from an Ubuntu boot disk. The laptop's hard drive is not mounted. I was also using a checksum to verify the backup against the hard drive like so:

```
$ dd if=/dev/sda of=/media/usbdrive/whatever.img
$ md5sum /dev/sda > laptop.md5
$ md5sum /media/usbdrive/whatever.img > img.md5 
```

Unfortunately over two separate attempts I have not gotten the checksums to match.

EDIT: However, I have mounted the dd image and retrieved part of the backup from the image, with no apparent corruption.

Are there any reasons other than data corruption that could be causing this? I have not tried to restore from said image to see if it "works" (for obvious reasons).

Thanks,
Eric

---

### Post by psusi on 2010-10-01
Ummm... if you are booting from that drive then it IS mounted, so things are changing while you try to copy.

And you shouldn't use dd like that.  If you want to image a drive, use something like clonezilla or ghost4linux, which you can find on the parted magic cd.

---

### Post by sippyCUP on 2010-10-16
> **psusi said:**
> Ummm... if you are booting from that drive then it IS mounted, so things are changing while you try to copy.

No, this.

"using DD while booted from an Ubuntu boot disk."

So I'm touching the hard drive via /dev/sda, not /media/disk.

But maybe I'll try some of those other tools as well.

---

