---
title: "Grub2 boot floppy to load Lubuntu from USB"
date: 2010-09-20
forum: General Help
---

### Post by wideyes on 2010-09-20
Hi all. This is not an original question by any means, but the many roads I have gone down haven't yielded results. I have a number of legacy pcs upon which I would like to install Lubuntu. None have CDROM drives, but they do have floppy drives. None can natively boot from USB devices. My goal is to boot into Grub2 from a floppy with USB support, but I'm having trouble making the floppy. I've seen recommended a few times a command string something like

```
grub-mkrescue --overlay=/boot/grub --image-type=floppy GRUB2.img
dd if=GRUB2.img of=/dev/fd0

```But when I go to do this, grub-mkrescue has no --overlay nor --image-type option. My man grub-mkrescue page only lists --modules and --output as options. I have managed to make a floppy using the commands
```
grub-mkrescue --output=FILE
dd if=FILE of=/dev/fd0 
```This disk does boot into Grub2. The problem with this is that I need to add other files to the disk to have USB functionality in Grub2, but this process writes to the floppy in iso9660 format, which mounts as read-only. I have tried to go this route using the mount -o remount option to try to make the fs rewritable, but I also haven't been successful with that (and I think my limited knowledge is restricting me here).

Maybe I can add the correct files to the file output by grub-mkrescue --output before I write it to the floppy, but I also don't know how to do that.

Basically, I'm a little burned out and looking for some direction. Am I going about this wrong? When I try and follow other people's guides, they seem to have options available to them that I don't have. I'm doing all this from my Lubuntu 10.04 live CD, but have found similar things on my regular Ubuntu 10.04 install as well.

Thanks in advance for your guidance.

---

### Post by cavalier911 on 2010-09-21
Install this on floppy to add USB boot capability on old hardware:
[http://www.plop.at/en/bootmanager.html](http://www.plop.at/en/bootmanager.html)
Install lubuntu with grub to USB.
Floppy will start plop which scans USB bus.When it finds USB grub takes over and boots lubuntu.

---

### Post by sikander3786 on 2010-09-21
There is an alternate method to boot of the USB if Bios doesn't support which I have been using in the past. See here.

[http://www.howtogeek.com/howto/16822/boot-from-a-usb-drive-even-if-your-bios-wont-let-you/](http://www.howtogeek.com/howto/16822/boot-from-a-usb-drive-even-if-your-bios-wont-let-you/)

---

### Post by wideyes on 2010-09-21
Thanks! Looks like another case of me making things harder than they needed to be. I was having trouble with the plop bootmanager going to a blank screen after trying to boot from USB, but revisited it after your suggestion and managed to get it working with some (seemingly arbitrary) futzing around in the options. Maybe it was a display issue. Anyway, thanks again - the lubuntu install is underway!

On an academic note, how does one go about using those (seemingly to me) 'extended' grub-mkrescue options? Do I have to install extra packages? I would like to have the functionality they seem to provide.

---

