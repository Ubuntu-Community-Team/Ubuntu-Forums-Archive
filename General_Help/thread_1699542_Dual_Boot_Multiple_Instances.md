---
title: "Dual Boot Multiple Instances"
date: 2011-03-03
forum: General Help
---

### Post by Rhetoric Camel on 2011-03-03
I took a picture with my camera of an issue I have when I start my computer. I have multiple instances of Ubuntu to load into. There are more now than when I took this picture, there are about 15 or so. I have no idea what I did or how to get rid of them all except the top one. All the others when I load into them don't run properly. Not sure why all these are here.

Any ideas on what this is about or what I can do to get rid of what I don't need?

---

### Post by wiggly81 on 2011-03-03
its showing older kernels, that is not a bad thing but you should be able to remove those with a command in terminal
```
sudo update-grub
```
that should create a new grub menu based on the current configuration

---

### Post by Rhetoric Camel on 2011-03-03
I did the command and this is what popped up afterwords

Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-29-generic-pae
Found initrd image: /boot/initrd.img-2.6.32-29-generic-pae
Found linux image: /boot/vmlinuz-2.6.32-29-generic
Found initrd image: /boot/initrd.img-2.6.32-29-generic
Found linux image: /boot/vmlinuz-2.6.32-28-generic-pae
Found initrd image: /boot/initrd.img-2.6.32-28-generic-pae
Found linux image: /boot/vmlinuz-2.6.32-28-generic
Found initrd image: /boot/initrd.img-2.6.32-28-generic
Found linux image: /boot/vmlinuz-2.6.32-25-generic-pae
Found initrd image: /boot/initrd.img-2.6.32-25-generic-pae
Found linux image: /boot/vmlinuz-2.6.32-25-generic
Found initrd image: /boot/initrd.img-2.6.32-25-generic
Found linux image: /boot/vmlinuz-2.6.32-23-generic-pae
Found initrd image: /boot/initrd.img-2.6.32-23-generic-pae
Found linux image: /boot/vmlinuz-2.6.32-23-generic
Found initrd image: /boot/initrd.img-2.6.32-23-generic
Found linux image: /boot/vmlinuz-2.6.32-22-generic-pae
Found initrd image: /boot/initrd.img-2.6.32-22-generic-pae
Found linux image: /boot/vmlinuz-2.6.32-22-generic
Found initrd image: /boot/initrd.img-2.6.32-22-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Microsoft Windows XP Home Edition on /dev/sda1
done

---

### Post by wiggly81 on 2011-03-03
yes, that is grub rebuilding the grub.cfg file, that is what controls the boot menu.

---

### Post by stinkeye on 2011-03-03
[**_[COLOR="DarkRed"]Ubuntu tweak [/COLOR]_**]("http://ubuntu-tweak.com/") is the easiest way to remove unwanted kernels.
It doesn't remove the current kernel so if you remove all but the latest 
shown in ubuntu tweak you'll be left with 2 kernels.
Recommended to have at least 2 kernels.
For each kernel there is 3 same numbered files to keep.
I am currently running 2.6.35-27 kernel and have kept 2.6.35-24 and 2.6.35-25 as shown in pic.


... and to customize grub2 see here: [**_[COLOR="#8b0000"]Grub Customizer[/COLOR]_**]("http://ubuntuforums.org/showthread.php?t=1664134")

---

### Post by Rhetoric Camel on 2011-03-04
Wiggly - I did that and restarted and all those are still in grub when I start up

Stinkeye - Thank you! That seemed to do the trick. And the Ubuntu Tweak is great.

---

