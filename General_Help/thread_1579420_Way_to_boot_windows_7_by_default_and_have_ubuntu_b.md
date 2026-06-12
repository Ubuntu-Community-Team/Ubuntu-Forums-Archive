---
title: "Way to boot windows 7 by default and have ubuntu boot from button press"
date: 2010-09-21
forum: General Help
---

### Post by legendarymidget on 2010-09-21
i was just wondering if there was any way to make it only boot ubuntu from pressing a button at startup like f11 or something instead of coming up with a menu asking me to choose which operating system to boot.

---

### Post by mikewhatever on 2010-09-21
There is a way to configure GRUB to do just that.

Run **less /boot/grub/grub.cfg | grep menuentry** . The output should show the menu entry for Windows7, for example

> menuentry "Windows Vista (loader) on dev/sda1"

You'll need the line inside the quotes in a second.

Open another terminal to edit /etc/default/grub:

```
sudo cp /etc/default/grub /etc/default/grub-backup

gksudo gedit /etc/default/grub
```

Modify the first line (GRUB_DEFAULT=0) to look like this:
GRUB_DEFAULT="Windows Vista (loader) on dev/sda1". Obviously, you'll need to use the line you got for your Windows installation. That should make sure to boot Windows by default.

Modify the second line (GRUB_HIDDEN_TIMEOUT=0), replacing the '0' with the desired timeout in seconds. You'll have to hit the 'Shift' key during the timeout to get to the boot menu.

Now, save and exit, and run **sudo update-grub** .

---

### Post by legendarymidget on 2010-09-22
thanks for the reply. i will try that

---

