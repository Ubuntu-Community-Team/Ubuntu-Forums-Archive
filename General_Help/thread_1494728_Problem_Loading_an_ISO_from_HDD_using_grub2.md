---
title: "Problem Loading an ISO from HDD using grub2"
date: 2010-05-27
forum: General Help
---

### Post by hotshot247 on 2010-05-27
i've read tutorials on how to do it and followed through perfectly but yet i still can't load an ISO from a hard drive using grub2. what i did was edited the 40_custom file in the /etc/grub.d folder but typing in the terminal "gksudo gedit /etc/grub.d/40_custom" and this is the contents of the 40_custom file, starting at "menuentry" is what i wrote:

#!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.

menuentry "Linux Mint 9 Live" {
       loopback loop (hd1,2)/home/chris/Downloads/linuxmint-9-gnome-dvd-i386.iso
       linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=/home/chris/Downloads/linuxmint-9-gnome-dvd-i386.iso file=(loop)/preseed/ubuntu.seed quiet splash bootkbd=sg --
       initrd (loop)/casper/initrd.lz
}

i even made it executable like the tutorial said by typing "sudo chmod +x /etc/grub.d/40_custom". the data is located on sdb2. it showed up on the grub2 menu but when i tried to boot from it, it told me something about unknown partition and unknown disk and something about the kernel needing to be first. i know the partition and the disk are right. it's on the second hard drive on the second partition. any help will be greatly appreciated! thanks!

---

### Post by gimfred on 2010-06-28
> **hotshot247 said:**
> i've read tutorials on how to do it and followed through perfectly but yet i still can't load an ISO from a hard drive using grub2. what i did was edited the 40_custom file in the /etc/grub.d folder but typing in the terminal "gksudo gedit /etc/grub.d/40_custom" and this is the contents of the 40_custom file, starting at "menuentry" is what i wrote:

#!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.

menuentry "Linux Mint 9 Live" {
       loopback loop (hd1,2)/home/chris/Downloads/linuxmint-9-gnome-dvd-i386.iso
       linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=/home/chris/Downloads/linuxmint-9-gnome-dvd-i386.iso file=(loop)/preseed/ubuntu.seed quiet splash bootkbd=sg --
       initrd (loop)/casper/initrd.lz
}

i even made it executable like the tutorial said by typing "sudo chmod +x /etc/grub.d/40_custom". the data is located on sdb2. it showed up on the grub2 menu but when i tried to boot from it, it told me something about unknown partition and unknown disk and something about the kernel needing to be first. i know the partition and the disk are right. it's on the second hard drive on the second partition. any help will be greatly appreciated! thanks!

I'm not sure about using loop to install iso. (obviously it works cos people have done it.) I couldn't workout what was needed in the iso-scan parameter.

My setup is such that I wanted to install to /dev/sda. I had room on /dev/sdb so created 8gb part on sdb. I used dd to write the iso to sdb 
```
sudo dd if=/home/me/Download/kubuntu-10.04-dvd-amd64.iso of=/dev/sdb1
```

then added this to 40_custom:

```
menuentry "KUbuntu 10.04" {
        set root=(hd1,1)
        linux /casper/vmlinuz boot=casper /preseed/kubuntu.seed
        initrd /casper/initrd.lz
} 

```
then did sudo chmod +x /etc/grub.d/40_custom, sudo update-grub2

I'm writing on the new 10.04 now :guitar:

---

### Post by hotshot247 on 2010-06-28
thanks! i'll check it out now.

---

