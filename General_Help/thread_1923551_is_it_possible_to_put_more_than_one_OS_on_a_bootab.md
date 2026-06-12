---
title: "is it possible to put more than one OS on a bootable USB ?"
date: 2012-02-10
forum: General Help
---

### Post by Gatorade on 2012-02-10
I'm planning to create a bootable USB flash drive because I was watching some tutorials and thought it would be kinda cool to try it out. I was just wondering , however, if its possible for me to put multiple linux OS on the flash drive (providing there's room on the drive.

Can anyone tell me if I would be able to do this , or am I restricted to one OS ?

---

### Post by brpylko on 2012-02-10
As long as they are all linux, that should work (Windows is possible, but in such a way that it only works if you boot off of a virtual hard disk linked to your usb stick inside a virtual machine).

---

### Post by lewmnik on 2012-02-10
Yes, you can have multiple OS on a USB, the same way as you can have them on a HDD. Before installing anything on your USB you need to create as many partitions as you would like to populate with different OSs.

---

### Post by Gatorade on 2012-02-10
cool, thanks,

---

### Post by C.S.Cameron on 2012-02-10
MultiBootUSB will allow you to put dozens of different Linux O/S on a Flash drive, (if it is large enough).

See:

[http://ubuntuforums.org/showthread.php?t=1518273](http://ubuntuforums.org/showthread.php?t=1518273)

---

### Post by xyzzyman on 2012-02-10
> **C.S.Cameron said:**
> MultiBootUSB will allow you to put dozens of different Linux O/S on a Flash drive, (if it is large enough).

See:

[http://ubuntuforums.org/showthread.php?t=1518273](http://ubuntuforums.org/showthread.php?t=1518273)

MultiSystem is also a nice one that I've been using:

[http://www.pendrivelinux.com/multiboot-create-a-multiboot-usb-from-linux/](http://www.pendrivelinux.com/multiboot-create-a-multiboot-usb-from-linux/)

I always have a few different distro's on the SD that I leave in my laptop, along with gparted live and hiren's boot cd on it.

---

### Post by Gatorade on 2012-02-12
hi guys , thanks for the suggestions. 

So, I gave multi-system a go and it seemed to have created the bootable flash drive with no problem , but now I'm having trouble setting my laptop to boot from USB. I hit F2 , got into the BIOS screen , but I don't see an option for me to set it to USB. Does anyone have the same laptop and know how to set it to boot from USB?

the laptop is an Asus n82jq , by the way.

---

### Post by Rex Bouwense on 2012-02-12
Check to see if the computer recogizes the flash drive as another hard drive.  My ASUS sees the flash drive as a hard drive as do some others.

---

### Post by Gatorade on 2012-02-12
I don't see it when I go into th BIOS, I only see the dvd drive and the laptop hard drive.

---

### Post by Rex Bouwense on 2012-02-12
Perhaps yours doesn't see it as another hard drive.  In my BIOS there is a + sign by hard drive and if I open it up, there is the flash drive.  My ASUS is an EeePC netbook so things could be different.  Sorry.

---

### Post by yetiman64 on 2012-02-12
> **Gatorade said:**
> I don't see it when I go into th BIOS, I only see the dvd drive and the laptop hard drive.

In my BIOS a usb drive will not show up under the "boot order" setting, it has to be left as HDD first. 

To boot from a usb drive I have to enter "boot priority" and move the usb stick entry up or down the order (top position to boot from it) there. There are also usb specific entries further in which allow to set the usb drive to emulate either a FDD or a HDD, I set mine to HDD emulation, though setting it to Auto may work as well (if the option is available). These settings here are not all in the one area, if you have similar you will need to check through the settings carefully. Good luck.

---

### Post by Gatorade on 2012-02-12
ok, I just tried it again and this time I found the USB drive, changed the boot order.

but it still won't boot into the USB drive.

---

### Post by Khayyam on 2012-02-13
All ...

I thought it worth mentioning that grub2 can also boot from iso's (loop devices), so you can effectively boot from as many images as will fit on the USB key.

```
menuentry "Ubuntu 11.10 Desktop-i386" {
 search --no-floppy --set -f /ubuntu-11.10-desktop-i386.iso
 loopback loop /ubuntu-11.10-desktop-i386.iso
 linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=/ubuntu-11.10-desktop-i386.iso quiet splash --
 initrd (loop)/casper/initrd.lz
}
menuentry "SystemRescueCD-x86 2.4.1" {
 search --no-floppy --set -f /systemrescuecd-x86-2.4.1.iso
 loopback loop /systemrescuecd-x86-2.4.1.iso
 linux (loop)/isolinux/rescuecd docache setkmap=us isoloop=systemrescuecd-x86-2.4.1.iso --
 initrd (loop)/isolinux/initram.igz
}
```HTH ..

---

### Post by Gatorade on 2012-02-13
I got some help on another forum where one of the guys told me I had to hold the ESC key after hitting the power button and that worked to boot the USB , and from there I was able to select the OS I wanted. I still could not get it to work, though. This is the message I got on the screen after it tried to boot the OS.

[IMG]http://i46.photobucket.com/albums/f143/Tortuga2112/Screenshot.jpg[/IMG]

anyone got any idea why its not working?

---

