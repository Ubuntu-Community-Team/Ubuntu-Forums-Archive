---
title: "Flash drive problems with Ubuntu live cd"
date: 2010-07-04
forum: General Help
---

### Post by COKEDUDE on 2010-07-04
I'm having difficulty with using my flash drive with the Ubuntu live cd. I see my flash drive but I can't access the flash drive. I have tried from both the gui and terminal. These are the commands that I used with the terminal. 
```
sudo mkdir /mnt/usb
sudo mount /dev/sda1 /mnt/usb

```

---

### Post by COKEDUDE on 2010-07-04
Does anyone have any ideas on what the problem is?

---

### Post by COKEDUDE on 2010-07-07
Ideas please?

---

### Post by COKEDUDE on 2010-07-12
Does anyone know what would cause this?

---

### Post by C.S.Cameron on 2010-07-12
Does it not show up in nautilus?

---

### Post by TechBeastie on 2010-07-12
Did the mount command seem to complete successfully, or did it just generate a large amount of usage information (indicating that it failed)?
Also, are you sure your flashdrive is actually /dev/sda1?  That's usually a partition on the primary system drive...

You might try using the print command in **parted** to double-check what the block device name (/dev/sd<something>) of the flash drive actually is.  

Finally, to check whether or not the flash drive is actually mounted correctly, you can use the **mount** command, which will show you a list of all mounted devices.

---

### Post by COKEDUDE on 2010-07-16
> **C.S.Cameron said:**
> Does it not show up in nautilus?

It shows up in Nautilus but I can't open or mount it. 

> **TechBeastie said:**
> Did the mount command seem to complete successfully, or did it just generate a large amount of usage information (indicating that it failed)?
**Also, are you sure your flashdrive is actually /dev/sda1?**  That's usually a partition on the primary system drive...

You might try using the print command in **parted** to double-check what the block device name (/dev/sd<something>) of the flash drive actually is.  

Finally, to check whether or not the flash drive is actually mounted correctly, you can use the **mount** command, which will show you a list of all mounted devices.

Oops your probably right. I probably didn't mount the right drive.

---

