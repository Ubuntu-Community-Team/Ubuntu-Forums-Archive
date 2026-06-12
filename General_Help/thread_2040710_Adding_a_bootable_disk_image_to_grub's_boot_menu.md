---
title: "Adding a bootable disk image to grub's boot menu"
date: 2012-08-11
forum: General Help
---

### Post by Lars Noodén on 2012-08-11
The new grub is fairly complex.  How would I find instructions on adding a file (/boot/floppy.img) to the boot menu?

---

### Post by Lars Noodén on 2012-08-12
I've found this:
[https://help.ubuntu.com/community/Grub2/CustomMenus](https://help.ubuntu.com/community/Grub2/CustomMenus)

but even with that, it is unclear how to add a disk image.

---

### Post by drs305 on 2012-08-12
By image do you mean a background image? GRUB accepts .png, .tga or 8-bit .jpg files. You can add an image to the /boot/grub folder and when you run 'update-grub' it will be added as the GRUB background.

[_https://help.ubuntu.com/community/Grub2/Displays#Installing_Splash_Images_]("https://help.ubuntu.com/community/Grub2/Displays#Installing_Splash_Images")

---

### Post by Lars Noodén on 2012-08-12
> **drs305 said:**
> By image do you mean a background image? GRUB accepts .png, .tga or 8-bit .jpg files. You can add an image to the /boot/grub folder and when you run 'update-grub' it will be added as the GRUB background.

[_https://help.ubuntu.com/community/Grub2/Displays#Installing_Splash_Images_]("https://help.ubuntu.com/community/Grub2/Displays#Installing_Splash_Images")

I am trying to boot a FreeDOS disk image so that I can update the BIOS on an old laptop that lacks a floppy drive.  It's old but not so old that it would still have a floppy.

---

### Post by drs305 on 2012-08-12
> **Lars Noodén said:**
> I am trying to boot a FreeDOS disk image so that I can update the BIOS on an old laptop that lacks a floppy drive.  It's old but not so old that it would still have a floppy.

Ok. The image (ISO) has to be constructed to allow GRUB to boot it. The Ubuntu family of ISOs has been GRUB-compatible for quite a while. I don't know if FreeDos is built to allow booting by Grub2 or not. 

Here is the documentation on booting an ISO via Grub2:
[https://help.ubuntu.com/community/Grub2/ISOBoot]("https://help.ubuntu.com/community/Grub2/ISOBoot")

I'll look at some of the posts in my old thread on the Ubuntu Forums and see if I can find a FreeDos entry.

---

### Post by Lars Noodén on 2012-08-12
> **drs305 said:**
> I'll look at some of the posts in my old thread on the Ubuntu Forums and see if I can find a FreeDos entry.

Thanks.  There's also a fair amount for Grub 1 and FreeDOS.  I might be able to figure out how to apply it to Grub 2.

---

### Post by drs305 on 2012-08-12
> **Lars Noodén said:**
> Thanks.  There's also a fair amount for Grub 1 and FreeDOS.  I might be able to figure out how to apply it to Grub 2.

I couldn't find a FreeDos entry in my main ISO booting thread. If you find it is bootable from G2 and get a working menuentry please let me know. I built a page on the Community documentation for working ISO menuentries and do not have one for FreeDos.

---

### Post by Lars Noodén on 2012-08-12
I've pieced together something that boots FreeDOS using notes from around the net.  The package syslinux needs to be installed and then memdisk copied to /boot, along with the FreeDOS image which I renamed to /boot/floppy.img.  Then I put the following into /etc/grub.d/41_custom used by update-grub:

```
cat <<EOT
menuentry "FreeDOS" {
    linux16 /boot/memdisk
    initrd16 /boot/floppy.img
}
EOT

```

I have no idea what I actually did, but it boots FreeDOS.

Edit: The whole point of this was to be able to update the BIOS on a machine lacking floppy drive.

---

### Post by drs305 on 2012-08-12
Thanks. Happy Ubuntu-ing and FreeDos-ing !

---

