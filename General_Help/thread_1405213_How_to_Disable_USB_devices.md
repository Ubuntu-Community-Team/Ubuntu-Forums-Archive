---
title: "How to Disable USB devices?"
date: 2010-02-12
forum: General Help
---

### Post by karthick87 on 2010-02-12
I would like to disable USB devices,so that i can restrict copying files from my system...How to do this???

---

### Post by nothingspecial on 2010-02-12
This will remove the driver that enables usb storage devices from the kernel to a hidden file in your root directory (well it won`t remove it from the kernel but it won`t get loaded next time you boot because it won`t be in the right place).
```

sudo mv /lib/modules/$(uname -r)/kernel/drivers/usb/storage/usb-storage.ko /.usb-storage.ko
```

That is in theory. I have never tried this. Do it at your own risk. It should work but ...........

---

### Post by karthick87 on 2010-02-12
How to get it work back?

---

### Post by nothingspecial on 2010-02-12
```
sudo mv /.usb-storage.ko /lib/modules/$(uname -r)/kernel/drivers/usb/storage/usb-storage.ko
``` 

and reboot.

You could disable usb in your bios.

I`d test this first. When you boot, do you still have some older kernels around?

Boot into one, do the command, reboot into the same kernel, put it back and reboot into it again to see if it works.

---

### Post by nothingspecial on 2010-02-12
I have just tested it for you (crazy fool that I am) and it appears to work.

In view of my sig

When you boot linux it loads all the drivers it needs from a certain directory.

That command moves the driver that makes usb storage devices work somewhere else so it won`t get loaded next time you boot.

The other command moves it back.

---

### Post by karthick87 on 2010-02-12
Great it works for me too..Thanks a lot buddy :D

---

