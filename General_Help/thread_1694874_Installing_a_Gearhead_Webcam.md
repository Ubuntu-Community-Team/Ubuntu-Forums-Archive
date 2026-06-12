---
title: "Installing a Gearhead Webcam"
date: 2011-02-25
forum: General Help
---

### Post by Noble720 on 2011-02-25
**I have been trying to follow these steps but I'm having problems with the third step. Every time I try to run "make mrproper" I get an error message. Help would be appreciated.** 

Step 1: Download latest kernel from official linux site.
Step 2: Extract the compressed file.
Step 3: Run “make mrproper”
Step 4: Copy your current config file in uncompressed source directory as .config.
Step 5: Run “make oldconfig”
Step 6: Edit drivers/media/video/gspca/pac7311.c file. Look for

{USB_DEVICE(0x093a, 0x2621), .driver_info = SENSOR_PAC7302},
and add one more line as shown below to add our device and save the file.

{USB_DEVICE(0x093a, 0x2620), .driver_info = SENSOR_PAC7302},
Step 7: Run “make all”, “make install” and “make modules_install” to install the kernel and all modules.
Step 8: If necessary create a initramfs also depends on your distribution.
Step 9: Make necessary changes to in the grub or lilo to point to your newly compiled kernel.
Step 10. Reboot and you should find dmesg identifying your device when you plug-in web cam.

---

### Post by Ditchdoc7893 on 2012-10-14
I actually just used cheese and got mine up and going.

sudo apt-get install cheese

---

