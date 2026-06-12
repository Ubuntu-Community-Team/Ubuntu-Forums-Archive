---
title: "Executable scripts from USB"
date: 2010-10-22
forum: General Help
---

### Post by leprosys on 2010-10-22
I can't change the permissions to script on my USB device, if the script is executable and I changed the permissions en my /home/user for example it works but when I copy the file again to my memory it is -x.

I try:
chmod 777 /media/usb/script
chmod +x /media/usb/script

As root and with my user but it doesn't work.

---

### Post by 666f6f on 2010-10-22
Does the USB filesystem support permissions? For instance, if your USB key is FAT formatted (very probable) you need to provide proper mount options for the scripts to become executable.

Alternatively you can run your scripts like this:

```
bash [script file]
```

**UPDATE:** Here's [how to provide mount options for removable devices (and much more)]("http://ubuntuforums.org/showthread.php?t=168221")

---

### Post by leprosys on 2010-10-22
Thanks, works :)

---

