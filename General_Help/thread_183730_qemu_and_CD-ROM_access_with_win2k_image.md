---
title: "qemu and CD-ROM access with win2k image"
date: 2006-05-28
forum: General Help
---

### Post by Shay Stephens on 2006-05-28
I have successfully installed qemu and it is booting up a windows 2000 image.  The CD-ROM shows up in "My Computer" but it does not see a disk once inserted.  Is there an option I am overlooking when running qemu?  Here is how I am currently running it from the command line:

```
qemu -hda win2k.img -m 256
```

Anyone with experience in this regard?  I need to load a cd/dvd thermal printer application that requires all kinds of windows only stuff.

---

### Post by tkjacobsen on 2006-05-29
you have to add the location of the cddrive:

```
qemu -hda win2k.img -m 256 -cdrom /dev/cdrom 
```


NOTES on win2k from qemu.org: (notice the `-win2k-hack' flag)
3.11.2.3 Windows 2000 disk full problem

Windows 2000 has a bug which gives a disk full problem during its installation. When installing it, use the `-win2k-hack' QEMU option to enable a specific workaround. After Windows 2000 is installed, you no longer need this option (this option slows down the IDE transfers).
3.11.2.4 Windows 2000 shutdown

Windows 2000 cannot automatically shutdown in QEMU although Windows 98 can. It comes from the fact that Windows 2000 does not automatically use the APM driver provided by the BIOS.

In order to correct that, do the following (thanks to Struan Bartlett): go to the Control Panel => Add/Remove Hardware & Next => Add/Troubleshoot a device => Add a new device & Next => No, select the hardware from a list & Next => NT Apm/Legacy Support & Next => Next (again) a few times. Now the driver is installed and Windows 2000 now correctly instructs QEMU to shutdown at the appropriate moment.

---

### Post by Shay Stephens on 2006-05-29
Thank you very much!!!  I tried it but got an error about not being able to load the image, so I swapped the options around, and got it to work.  This line boots win2k and makes the CD available:

```
qemu -hda win2k.img -cdrom /dev/cdrom -m 256
```

The caveat is you have to have the CD installed in the drive before starting qemu and you can't change the CD during the session or the second cd will never show up as available.  But at least now I can try to install some software :-D

Thanks again!

---

### Post by tkjacobsen on 2006-05-29
Im actually not very familiar with qemu. But you only have to set the -cdrom when booting from the disc. It is possible (I don't know exactly how) to mount discs from the qemu manager (ctrl + alt + 2 inside qemu). Switch back to the emulation mode with ctrl +alt +1. (there also is some ctrl+alt+3 mode, but Í don't know what it does.

---

