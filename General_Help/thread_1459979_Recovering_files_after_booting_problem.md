---
title: "Recovering files after booting problem"
date: 2010-04-22
forum: General Help
---

### Post by Tomasz_sz on 2010-04-22
I'm currently running ubuntu 9.10 on my laptop, but when I try and boot it stops after the line:

fsck from util-linux-ng 2.16
/dev/sda1: clean .../... files .../... blocks

(numbers in the place of ...)

I can boot from a live usb, and I would just reinstall ubuntu but I can't access all of the files in my home folder and I'd rather not lose them. It says I don't have the necessary permissions to view them.

Any help in either getting my original installation to work again or in getting access to my files would be great appreciated.

Cheers,

Tom

---

### Post by nothingspecial on 2010-04-22
You need to use sudo to copy them

either ```
gksudo nautilus
``` then drag and drop

or ```
sudo cp -r /mount_point_of_harddrive/home/username /mount_point_of_external_media
```

When you copy those files back to your new system you will have to change the ownership back to your user

---

### Post by Tomasz_sz on 2010-04-22
Ok that worked.

Thanks a lot.

---

