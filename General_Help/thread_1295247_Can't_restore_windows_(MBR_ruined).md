---
title: "Can't restore windows (MBR ruined)"
date: 2009-10-19
forum: General Help
---

### Post by martinrandau on 2009-10-19
I have two hard drives on a desktop computer: /dev/sda and /dev/sdb

At first I decided to install ubuntu on sdb and leave windows on sda. Ubuntu installed fine but I could not launch windows. I think what I did was to choose to install grub on /dev/sdb instead of hd0 (default option). That was a mistake I think.

Now I can't get windows back. I have tried to install ubuntu on sda (leaving sdb as a pure unmounted ext4 file system). The installer detects windows there and it's available at boot, but choosing it leaves me with a 

```
GRUB
```

menu and nothing more.

I tried to use 
```

sudo ms-sys -mbr /dev/sda
```

but I still get the GRUB thingy when choosing windows.

Any ideas? I can access the windows partition from my ubuntu install.

Also, the wireless does not work on ubuntu so all changes need to be done using a usb-drive.

---

### Post by wild_oscar on 2009-10-19
You can always boot windows from disk and, in the recovery console, fixmbr:

[http://askbobrankin.com/fix_mbr.html](http://askbobrankin.com/fix_mbr.html)

---

### Post by martinrandau on 2009-10-19
Yes I will download some-tool-to-fix-mbr.iso and create a usb startup disk and see if I can fix it.

Thanks for the tip! :)

---

