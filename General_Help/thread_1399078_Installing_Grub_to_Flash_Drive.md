---
title: "Installing Grub to Flash Drive"
date: 2010-02-05
forum: General Help
---

### Post by bnshrdr on 2010-02-05
Alright, I have read a lot of tutorials on how to do this, but these all assume that you have an existing linux partition on the drive as well.  I realize that I probably would at least need the kernel, but I have yet to find a tutorial that shows me how to do this partition independent.

Also, if this is in the wrong forum, feel free to move it.

Thanks!

---

### Post by audiomick on 2010-02-05
A bit more info please.
What exactly do you want to do, and what do you want to achieve with that?

---

### Post by ajgreeny on 2010-02-05
If we assume that you can run ubuntu from wherever it is installed, you should be able to install that version's grub (legacy grub in 9.04 and earlier, grub2 in 9.10 and later) simply by booting to the ubuntu and using the command ```
sudo grub-install /dev/sdx
``` where the x is whatever the flash disk is named by the system.  Don't use a partition name, just the disk dev name.

I don't think it will matter what else is (or isn't) on that flash disk as grub will be put on the first sector of the disk, away from everything else, but if you have important files on it make sure you back up first.

---

### Post by bnshrdr on 2010-02-05
Thanks for the replies.

I ended up having to run this
```
sudo grub-install --recheck /dev/sdb
```

And it said it installed it successfully, but when I boot to it, all I see if a dark screen with the word GRUB in the upper left corner.  Does this mean it was successful and I need to configure it?  If so, how do I configure it because when I view the partitions via ubuntu, nothing shows up.

Edit:  Just a thought.  I have grub installed successfully on my computer hdd as well.  Could I do something like this?
```
sudo dd if=/dev/sda1 of=/dev/sdb1
```
Of course I'd have to change the menu.lst

---

### Post by Megaptera on 2010-02-05
Hi,
Have you tried one of these options? Is this what you're looking to do?

[http://www.pendrivelinux.com/](http://www.pendrivelinux.com/)

---

### Post by bnshrdr on 2010-02-05
I plan on having about 5 different utilities that I can boot to and I want to use grub to send me to each of them if I so choose.  Plus this will be kind of a learning experience for me.

---

### Post by Megaptera on 2010-02-05
Perhaps this multi-boot option on USB?

[http://www.pendrivelinux.com/boot-multiple-iso-from-usb-multiboot-usb/](http://www.pendrivelinux.com/boot-multiple-iso-from-usb-multiboot-usb/)

---

### Post by VMC on 2010-02-05
> **bnshrdr said:**
> Thanks for the replies.

I ended up having to run this
```
sudo grub-install --recheck /dev/sdb
```

And it said it installed it successfully, but when I boot to it, all I see if a dark screen with the word GRUB in the upper left corner.  Does this mean it was successful and I need to configure it?  If so, how do I configure it because when I view the partitions via ubuntu, nothing shows up.

Edit:  Just a thought.  I have grub installed successfully on my computer hdd as well.  Could I do something like this?
```
sudo dd if=/dev/sda1 of=/dev/sdb1
```
Of course I'd have to change the menu.lst
That dd command won't work unless the HD are the same.

Also you need to chroot to the drive in question then issue the 'grub-install' command.

---

### Post by dbowlin17 on 2010-02-05
just to try and make this clear, you want to have multiple utilities on one thumb drive and want a bootloader (grub) to select each one?

---

### Post by bnshrdr on 2010-02-05
Well I'll configure it to see them, I just need to get my freaking thumb drive bootable.

Ok, so I had cd'd into the only partition, a 20 MB fat16 partition, and ran grub-install /dev/sdb, and it said it succeeded.  If I boot to it though, it says welcome to grub and then it said something about rescue mode and then booted to the next disk.  I then went and viewed the partition and can't view any files that pertain to configuration.

---

