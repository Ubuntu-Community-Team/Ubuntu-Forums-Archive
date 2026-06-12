---
title: "fsck at startup"
date: 2009-09-29
forum: General Help
---

### Post by J V on 2009-09-29
I ran a command to run fsck at startup to check disk fragmentation... Now it runs every time and adds a lot of boot time, anyone know how to stop this?

Also, how do I get the wubi menu to shorten, 10 seconds takes forever...

---

### Post by langi280179 on 2009-09-29
If the device is clean, fsck should only be activated at boot time if the maximum number of counts is reached. So i would try to do set

```

tune2fs -c 30 /dev/sdxx

```

This resets the number of mounts to 30 which is a usual value.

I don't know what the wubi menu is, but i expect it to be a grub menu. In this case edit /boot/grub/menu.lst and set 

```

timeout         3 

```

for 3 seconds wait time.

regards,

markus.

---

### Post by J V on 2009-09-29
No, fsck runs every single boot... I will try the "grub" timer, but I don't think it works on wubi

---

### Post by langi280179 on 2009-09-29
before, during or after fsck no error messages?

---

### Post by langi280179 on 2009-09-29
> **J V said:**
> I will try the "grub" timer, but I don't think it works on wubi

You are propably right. Wubi does not install grub as bootloader

---

