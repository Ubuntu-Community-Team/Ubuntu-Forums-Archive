---
title: "Can't see iso image on dvd, don't want contents"
date: 2010-04-14
forum: General Help
---

### Post by drreed on 2010-04-14
Someone please enlighten me. I'm trying to run unetbootin to install 8.10 on a usb stick. When I run the app, and try to select the iso image, a file selection dialog opens and shows me only the contents of the iso, not the iso. I can't even tell what the name of the iso image is.  I've had this problem before, but it wasn't critical so I went to work on somethign else. It's now time to figure this out because it's frustrating and confining.

---

### Post by ttshivers on 2010-04-14
Make sure that the "disk image" selection is selected and also make sure that the image type is ISO not IMG.  Also, after you run Unetbootin, the usb stick will show the contents of the extracted iso image, which is what you need to be able to run ubuntu from it.  You need to reboot your computer and boot from the usb stick to be able to run ubuntu.

---

### Post by drreed on 2010-04-14
> **ttshivers said:**
> Make sure that the "disk image" selection is selected and also make sure that the image type is ISO not IMG.  Also, after you run Unetbootin, the usb stick will show the contents of the extracted iso image, which is what you need to be able to run ubuntu from it.  You need to reboot your computer and boot from the usb stick to be able to run ubuntu.

I tried that, no luck.



Just found this:

mount -o loop myimage.iso /path/directory 

The problem is, I don't know what the image is called.

---

### Post by ttshivers on 2010-04-15
The iso name for the regular ubuntu 8.10 cd is "ubuntu-8.10-desktop-i386.iso"

---

### Post by drreed on 2010-04-15
> **ttshivers said:**
> The iso name for the regular ubuntu 8.10 cd is "ubuntu-8.10-desktop-i386.iso"


What would be the full path name to that file?

---

### Post by ttshivers on 2010-04-16
If the iso image is in the Downloads folder, then the path would be:   ```
/home/travis/Downloads/ubuntu-8.10-desktop-i386.iso
```

---

### Post by drreed on 2010-04-16
> **ttshivers said:**
> If the iso image is in the Downloads folder, then the path would be:   ```
/home/travis/Downloads/ubuntu-8.10-desktop-i386.iso
```

The iso image is on a cd in my cd/dvd-rw drive, referenced multiple ways . . .

Konquerer calls it /media: 
but I don't know what to put after that

The block device is called something else, like /dev/cd0 or something, and I can't see it when I display the directory for some reason.

I also have a /cdrom (which is a link) in my root folder.

It seems like I shouldn't have to know the name of the iso anyway -I should be able to list it in a directory, or see it in Konquerer, with the full path in the address bar. 

In Windows, all I have to do is open the drive in file manager and there it is in all it's glory. I have to double-click on that iso, and have a iso utility, to see the contents. An annoyance sometimes, but certainly not when it's the iso I want to work with!

I find it hard to believe linux can't display the name of an iso file, with the full path to it's location. There should be 10 ways to do this.

---

### Post by ttshivers on 2010-04-16
Yes, I really agree.  Linux should be able to do that much easier than Windows.

> **drreed said:**
> The iso image is on a cd in my cd/dvd-rw drive, referenced multiple ways . . .

Konquerer calls it /media: 
but I don't know what to put after that

The block device is called something else, like /dev/cd0 or something, and I can't see it when I display the directory for some reason.

I also have a /cdrom (which is a link) in my root folder.

It seems like I shouldn't have to know the name of the iso anyway -I should be able to list it in a directory, or see it in Konquerer, with the full path in the address bar. 

In Windows, all I have to do is open the drive in file manager and there it is in all it's glory. I have to double-click on that iso, and have a iso utility, to see the contents. An annoyance sometimes, but certainly not when it's the iso I want to work with!

I find it hard to believe linux can't display the name of an iso file, with the full path to it's location. There should be 10 ways to do this.

---

