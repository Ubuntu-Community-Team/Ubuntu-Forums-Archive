---
title: "Unable to make Clonezilla live USB drive"
date: 2010-12-05
forum: General Help
---

### Post by gunit888 on 2010-12-05
I've tried using UNetBootin to create a Clonezilla bootable USB drive so I can take an image of my system.  However, when I book, I get "Operating System Missing" and it immediately moves on to the bootloader that I usually get.

I've also tried using Startup Disk Creator, but when I select the Clonezilla .iso file, it doesn't actually select anything in the source ISO window.

I'm pretty stuck here, I don't know what else I can do.  I can't burn a CD so I have to create a bootable USB drive.

---

### Post by davidmohammed on 2010-12-05
have you been following [this guide]("http://clonezilla.org/clonezilla-live/liveusb.php")?

---

### Post by C.S.Cameron on 2010-12-05
MultiBootUSB works with clonezilla:

[http://ubuntuforums.org/showthread.php?t=1518273](http://ubuntuforums.org/showthread.php?t=1518273)

---

### Post by gunit888 on 2010-12-06
@C.S. Cameron - I have been trying MultiBootUSB this morning, I get "error: cannot find file" and it refuses to boot -> [http://ubuntuforums.org/showthread.php?t=1518273&page=9]("http://ubuntuforums.org/showthread.php?t=1518273&page=9@davidmohammed")

@davidmohammed - I tried the UNetBootin directions, but I'll give the manual command line method a shot.

---

### Post by gunit888 on 2010-12-06
@davidmohammed - I tried the series of manual instructions, with no luck.  The first time I booted up and got a line reading "SYSLINUX 4.03" and a date and a copyright, the next line was a blinking cursor, and that's all it did.  I tried setting up the usb drive again, using the suggestion of 'syslinux -fs /dev/sdc1' as the makeboot.sh script suggested I try.  This did the same thing, except it was "SYSLINUX 4.01".

---

### Post by C.S.Cameron on 2010-12-06
> **gunit888 said:**
> @C.S. Cameron - I have been trying MultiBootUSB this morning, I get "error: cannot find file" and it refuses to boot -> [http://ubuntuforums.org/showthread.php?t=1518273&page=9]("http://ubuntuforums.org/showthread.php?t=1518273&page=9@davidmohammed")

@davidmohammed - I tried the UNetBootin directions, but I'll give the manual command line method a shot.

Confirm that the path listed in grub.cfg is the actual path to the kernel.

---

### Post by twitty1437 on 2010-12-06
I tried doing it with UNetBootin on Ubuntu and it didn't work, but when i make it from XP using UNetBootin. it works.

---

### Post by gunit888 on 2010-12-07
Finally, I got it all straightened out.  First, thank you C. S. Cameron, I was so deep in the weeds that I didn't even think to check that.  It turns out that the name of the file was different than the grub config was looking for.  Second, after changing that, I got a new set of problems, but eventually discovered that there was a missing boot parameter.  I'm guessing that MultiBootUSB simply wasn't updated with the latest changes done to Clonezilla.  I was finally able to fire up Clonezilla and image my laptop.

Here's the grub menu entries I have that got it working, in case anyone else runs into this problem.  The changes I had to make are in **bold**.  

```

    menuentry "Clonezilla" {
        loopback loop /boot/iso/clonezilla-live-1.2.6-40-i686.iso
        linux (loop)/live/vmlinuz**1** root=(loop)/ rootfstype=loop findiso=/boot/iso/clonezilla-live-1.2.6-40-i686.iso quickreboot utc=no    boot=live** config** union=aufs noswap nolocales edd=on ocs_live_run="ocs-live-general" ocs_live_extra_param="" ocs_live_keymap="NONE" ocs_live_batch="no" ocs_lang="en_US.UTF-8" ocs_daemonon="ssh" ocs_numlk=on ip=frommedia nosplash
        initrd (loop)/live/initrd**1**.img
    }

    menuentry "Clonezilla - To RAM" {
        loopback loop /boot/iso/clonezilla-live-1.2.6-40-i686.iso
        linux (loop)/live/vmlinuz**1** root=(loop)/ rootfstype=loop findiso=/boot/iso/clonezilla-live-1.2.6-40-i686.iso quickreboot utc=no toram=filesystem.squashfs   boot=live** config** union=aufs noswap nolocales edd=on ocs_live_run="ocs-live-general" ocs_live_extra_param="" ocs_live_keymap="NONE" ocs_live_batch="no" ocs_lang="en_US.UTF-8" ocs_daemonon="ssh" ocs_numlk=on ip=frommedia nosplash
        initrd (loop)/live/initrd**1**.img
    }

```Please note that this is in particular for Clonezilla 1.2.6-40, but based on what I've learned, I believe it should work for the 20101130-maverick.iso as well.  I was working with MultiBootUSB Beta 3.2.0 to generate the live usb itself, and then modified the config afterwards.  I still don't quite get why they added the number 1 to the end, but there ya go.

---

