---
title: "How to copy complete OS on USB stick?"
date: 2011-07-04
forum: General Help
---

### Post by bobc2 on 2011-07-04
I have Ubuntu 10.10 installed on a 4GB USB stick. I need to make a full bootable backup copy of the OS onto another 4GB USB stick.

I have a DVD burner installed, but no hard drive.

What's best way to do this?

Thanks,

--Bob

---

### Post by e79 on 2011-07-04
I'd try with [CloneZilla]("http://clonezilla.org/")

Hope this helps

---

### Post by bobc2 on 2011-07-04
> **e79 said:**
> I'd try with [CloneZilla]("http://clonezilla.org/")

Hope this helps

That worked great. Thanks for the quick response!

--Bob

---

### Post by sidzen on 2011-07-04
[COLOR=Navy]Insert your USB stick(s) and learn how it(they) is(are) recognized by the system, To do so, enter the command:
[/COLOR][COLOR=Navy]
[/COLOR][INDENT] [COLOR=Navy]    sudo ls -l /dev/disk/by-id/*usb*[/COLOR][COLOR=Navy]     
[/COLOR] [/INDENT][COLOR=Navy]
   This should produce output along the lines of:

[/COLOR][INDENT] [COLOR=Navy]    lrwxrwxrwx 1 root root  9 2010-03-15 22:54 /dev/disk/by-id/usb-_USB_DISK_2.0_077508380189-0:0[/COLOR][COLOR=Navy]
[/COLOR] [COLOR=Navy]    -> ../../sdb    (or sdc, sdd, etc.)

[/COLOR] [COLOR=Navy]    lrwxrwxrwx 1 root root 10 2010-03-15 22:54 /dev/disk/by-id/usb-_USB_DISK_2.0_077508380189-0:0-
    part1 -> ../../sdb1[/COLOR][COLOR=Navy]
[/COLOR] [/INDENT][COLOR=Navy]
Unmount the target usb stick  (NOTE: replace the X in sdX with whatever was returned for target USB stick)
   from command above)
[/COLOR][COLOR=Navy]
[/COLOR][INDENT] [COLOR=Navy]    sudo umount /dev/sdX[/COLOR][COLOR=Navy]
[/COLOR] [/INDENT][COLOR=Navy]
Use this command to write (as root) the image iso to your USB stick:

[/COLOR][INDENT] [COLOR=Navy]    dd if=/path/to/your/distro.iso of=/dev/sdX bs=4M;sync[/COLOR][COLOR=Navy]
[/COLOR] [/INDENT][COLOR=Navy]
[/COLOR]

---

### Post by e79 on 2011-07-04
> **bobc2 said:**
> That worked great. Thanks for the quick response!

--Bob

The pleasure is all mine  :p

Regards

---

