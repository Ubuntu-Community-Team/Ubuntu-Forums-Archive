---
title: "GRUB2 on partition (not MBR)"
date: 2010-01-20
forum: General Help
---

### Post by R3N3G4D3 on 2010-01-20
I tried searching for this both in the forums and on google but it seems that everything goes back to MBR installation. I know that "grub-install /dev/sda1" should install it to the sda1 partition, but instead of installing it keeps giving me the following error:
```
grub-probe: error: cannot find a device for /boot/grub.

No path or device is specified.
Try ``grub-probe --help'' for more information.
Auto-detection of a filesystem module failed.
Please specify the module with the option `--modules' explicitly.
```

I tried this with a fresh installation of Karmic on both of my PCs. I tried with --recheck option as well, same error. Installing it to MBR works fine, but I don't want it there, have another bootloader chainloading grub. Every single guide I found installs GRUB2 to MBR, and some briefly reference to "grub-install /dev/sdaX" without going into any detail.

At first I thought the problem was because Ubuntu was installed on a logical partition, so I created a separate /boot partition and formatted it as ext2, still getting the same problem.

Thanks

---

### Post by synapsys on 2010-01-20
Looks like you want to use **grub-setup** here's a guide:

[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_to_a_Partition]("http://members.iinet.net/%7Eherman546/p20/GRUB2%20Bash%20Commands.html#GRUB_to_a_Partition")

---

### Post by ranch hand on 2010-01-20
It is not a good idea to install grub to a partition.  I am surprised, however, that grub1.97beta4 will not do it.  That is what is in 9.10.

I am not sure about 1.97 (was in 10.04 testing) but I know that 1.98 (is in 10.04-testing) will not do it.

In 9.10 you should be getting a warning message about it being a bad thing to do as it is being done.

You might try removing grub-common and grub-pc and reinstalling them.  Obviously you should not reboot or shut down until this is finished.  Then try it again.

I would use grub as your bootloader, myself, because I think it is the best.  The box this is on is your box though so have at it.

---

### Post by R3N3G4D3 on 2010-01-20
I don't mind using grub, but I'm trying to dual-boot Mac as well and when launching OSX through grub2, it kernel panics and reboots. When using chameleon as main bootloader, it boots fine, but chameleon will not boot Linux natively, only through chainloading grub (and requires grub to be on a partition rather than MBR). Based on my searches, everyone who got grub working with chameleon seems to use legacy grub. I do get a warning like you mentioned when specifying --root-directory option, but then I also get an error about core.img

---

### Post by Leppie on 2010-01-20
apparently it is possible to boot mac osx from grub2.
you'll need a menu entry like this:
```
menuentry "Mac OS X" {
    set root=(hdX,Y)
    insmod video
    insmod vbe
    gfxmode="1280x800x32"
    xnu_kernel /mach_kernel rd=diskXsY
    if [ /System/Library/Extensions.mkext -nt /System/Library/Extensions ]; then
       xnu_mkext /System/Library/Extensions.mkext
    else
       xnu_kextdir /System/Library/Extensions
    fi
}
```
you may want to check the gfxmode, etc.

---

### Post by R3N3G4D3 on 2010-01-21
Leppie, grub2 actually automatically added something very similar to what you provided when I ran "grub-update" a while back. And that's how I tried booting OSX a few times, it would start loading OSX, but would reboot because of kernel panic.

I finally installed grub on a partition with the help of the guide synapsys provided. I actually saw it a while back, but I got device.map error and figured the solution didn't work either. However, I tried it again after binding my Linux's /boot directory to LiveCD /boot, and used the --force flag to install grub, and it worked.

---

