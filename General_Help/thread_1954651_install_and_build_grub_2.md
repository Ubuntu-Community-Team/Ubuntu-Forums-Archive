---
title: "install and build grub 2"
date: 2012-04-08
forum: General Help
---

### Post by bobman321123 on 2012-04-08
I have several systems on my hardrive, (openSUSE, Fedora, Ubuntu, linuxmint, arch, etc etc) and all of them try to install their own bootloader, and it's getting frustrating. 
Is there a way I could install and populate one master bootloader?
Preferably GRUB 2, but GRUB will work if needed. 

Thanks for your help!

---

### Post by Cheesemill on 2012-04-08
One way to do it is to choose one 'master' OS which has control of the main bootloader stored in the MBR.

The when installing all of the other distros, instead of having them install a bootloader to the MBR, have them install their bootloader into their own / partition.

These bootloaders can then be chainloaded from the one installed in the MBR.

This method has the advantage that each bootloader is updated and managed by its OS's own package management tools.

---

### Post by oldfred on 2012-04-08
With grub legacy, I had a grub only partition and chainloaded everything. But grub2 does not like to be installed to a partition. I did it with 9.10 but it complained and after I learned about grub2, I find using grub2 just to work.

If your other install has grub legacy, I would install it to its root (or boot if /boot is required) partition. Otherwise you can directly boot from grub2 into just about every other system.

Grub2's os-prober which runs as part of sudo update-grub finds all other systems and lets you directly boot them (not chain). So like Cheesemill's suggestion select one install with grub2 as the master and let it update to boot every other install. The disadvantage is that you have to reboot into the master and rerun the sudo update-grub to see new kernels in other installs. But there are workarounds to directly boot a partition if Debian based that has links in / (root) to the most current kernel. And you can still add chainload entries if the other install has grub legacy.

If you decide to have a grub2 only partition you have to manually maintain it as there are no support scripts. I do have this type of grub2 in my flash drives to boot ISO and add entries to boot hard drive just as a backup.

The Grub 2 Guide - drs305 also link to grub customizer
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

Grub 1.99 40_custom
Does not like typos,changed root to set root, cannot have echo, cat, EOF lines
[http://ubuntuforums.org/showthread.php?t=1746868](http://ubuntuforums.org/showthread.php?t=1746868)

You can add a entries like thisto 40_custom:
Boot most up2date kernel on sda7
```
menuentry "Install on sda7" {
    set root=(hd0,7)
        linux /vmlinuz root=/dev/sda7 ro quiet splash
        initrd /initrd.img
}
menuentry "Chainload Other Systems Grub Menu on sdc1" {
set root=(hd2,1)
chainloader +1
}

menuentry " " {
set root= 
}

menuentry "Reboot" {
    reboot
}

```

---

### Post by bobman321123 on 2012-04-08
> **Cheesemill said:**
> One way to do it is to choose one 'master' OS which has control of the main bootloader stored in the MBR.

The when installing all of the other distros, instead of having them install a bootloader to the MBR, have them install their bootloader into their own / partition.

These bootloaders can then be chainloaded from the one installed in the MBR.

This method has the advantage that each bootloader is updated and managed by its OS's own package management tools.

Thanks a bunch!
I fixed the location of the bootloader using "Rescatux", and ran update-grub and it fixed it all. :D

Thanks, again.

---

