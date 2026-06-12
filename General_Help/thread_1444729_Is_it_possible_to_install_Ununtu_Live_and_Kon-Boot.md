---
title: "Is it possible to install Ununtu Live and Kon-Boot on same USB Flash Drive??"
date: 2010-04-01
forum: General Help
---

### Post by taylormah on 2010-04-01
I wanted to keep kon-boot and ubuntu live on USB drives instead of CDs for the ease of carrying around. I wonder if its at all possible to put both tools on same USB drive instead of keeping them on two separate ones? Any idea folks?

---

### Post by johngreth on 2010-04-01
It is possible, but difficult. I started writing an article about it on my blog a month ago and still haven't finished because it's so complicated. Basically you need to format the flash drive, install Syslinux on it, put the files from both live cds on it, and configure Syslinux to work with both.

---

### Post by vaniaspeedy on 2010-05-11
Yes, it is possible. Here is what you need to do.
1. Install ubuntu to the USB (many tutorials on the net, try
    [http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/](http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/)
    
2. The, go to syslinux/test.cfg. You will see these lines:

label live
  menu label ^Try Ubuntu without any change to your computer
  kernel /casper/vmlinuz
  append  file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.lz quiet splash --

3. That's what you want. Now, under this line, add this:
LABEL grub
Menu label ^Grub
KERNEL /grub.exe

4. Now, download grub4dos.zip from here:
[http://dl.dropbox.com/u/6305346/grub4dos.zip](http://dl.dropbox.com/u/6305346/grub4dos.zip)

5. Extract the files to the root of the USB.

6.Now, save the changes, and reboot.

In a nutshell, this is what will happen at the boot. 
Syslinux loads all of the files into the menu, including txt.cfg
txt.cfg loads grub.exe,
 which loads menu.lst,
 from which you can load konboot, your OS, windows, ISO's, etc. 

If you have any questions, just ask!

EDIT: @johngreth

Hey, I posted a short summary of what to do. Syslinux has trouble loading KonBoot, use grub instead. Feel free to use the info in your article, just give due credit. ( My name is VaniaSpeedy)

---

### Post by vaniaspeedy on 2010-05-11
EDIT:
Just found my mistake. at step three, add these lines instead

LABEL KonBoot
MENU LABEL KonBoot
KERNEL /memdisk.konboot
APPEND initrd=/konboot.img

Then go to [http://dl.dropbox.com/u/6305346/grub4dos.zip](http://dl.dropbox.com/u/6305346/grub4dos.zip)
Extract memdisk.konboot and konboot.img, and then put them into the root of your USB. Done!

---

