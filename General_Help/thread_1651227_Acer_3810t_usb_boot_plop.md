---
title: "Acer 3810t usb boot plop"
date: 2010-12-22
forum: General Help
---

### Post by dollzii on 2010-12-22
Hey!
Just got my computer back from repair, when I try booting it up in ubuntu i get the message;

```
Target filesystem doesn't have /sbin/init
```

Then I get a shell. Google'd it and found out I have to boot a live CD, but now I have problems getting it to boot my USB. Had some problems with this when I first installed Ubuntu, but I managed to boot with Plop Boot Manager.

According to the plop website it can be used with GRUB2, the problem is how can I install it? 

> Download the current boot manager plpbt-5.0.11.zip. Extract it to get the boot manager binary program plpbt.bin.

Copy the plpbt.bin file to /boot.

You have to choose the correct root settings in grub.cfg for your system.
The following is an example

menuentry "Plop Boot Manager" {
    set root=(hd0,1)
    linux16 /boot/plpbt.bin
}

When you reboot, you should be able to start the boot manager from your grub menu.

Any ideas ?

---

