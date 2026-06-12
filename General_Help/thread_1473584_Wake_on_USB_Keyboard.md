---
title: "Wake on USB Keyboard"
date: 2010-05-05
forum: General Help
---

### Post by Melk79 on 2010-05-05
I had wake from sleep using my wireless usb keyboard under 9.10, but since upgrading to 10.04 I can no longer get it to work.  I followed these steps from another post:
USB Keyboard wake from suspend:

([http://ubuntuforums.org/showthread.php?t=711747&page=2]("http://ubuntuforums.org/showthread.php?t=711747&page=2"))

Type into the terminal to list the devices:

Code:

```
cat /proc/acpi/wakeup
```

You will probably find your USBX is disabled, to enable it create a file in /etc/init.d by going:

Code:

```
sudo nano /etc/init.d/wake.sh
```

Then add the following to the new file (making sure you update the USB number):

Code:

```
sudo -s
echo USB4 > /proc/acpi/wakeup
```

CHMOD the file to excute:

Code:

```
sudo chmod +x /etc/init.d/wake.sh
```

Lastly tell Ubuntu to excute on boot:

Code:
```

sudo update-rc.d wake.sh defaults
```


It doesn't work on restart.  I'm curious if there is a simple way of doing this in a gui or gconf-editor.   Does any one know?  I've searched and searched, but mostly people seem to resort to writing this script.  Bugs that exist for this issue end with a recommendation for using acpitools.  While that can easily echo the wakeup file for USB, it also doesn't retain that behavior after restart.  Any ideas?

---

### Post by dino99 on 2010-05-05
on my system its a bios setting choice, then with ubuntu its depend how the keyboard is identified and its settings done (third level, ...) and the language selected.

you may watch logs to see if the keyboard is well recognized first before to modify scripts

---

### Post by Melk79 on 2010-05-05
I do have that setting made in my BIOS as well.  But the output of 'cat /proc/acpi/wakeup' shows USB4 as disabled.

---

### Post by dino99 on 2010-05-05
not sure but try:

sudo gedit /etc/default/grub

search the line with "quiet splash" and add "acpi=force" in it

then sudo update-initramfs -u
sudo grub-mkconfig && update-grub

---

