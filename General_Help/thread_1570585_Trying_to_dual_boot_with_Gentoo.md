---
title: "Trying to dual boot with Gentoo"
date: 2010-09-08
forum: General Help
---

### Post by M4rotku on 2010-09-08
Hey guys,

I recently installed Gentoo onto a second partition (sda2) and am having trouble with grub.  I want Ubuntu to control grub (I thought it would be easier than manually writing it via Gentoo.)  From what I read, it seemed like I just needed to run the update-grub command and it would automatically be detected and added.  Well, the command managed to detect the Gentoo base system on partition sda2, but for some reason it didn't add it to the boot menu.  Do I have to run another command for it to be added?  Is there anything else I need to do?

Much thanks,
M4rotku

---

### Post by hyperAura on 2010-09-08
You can try adding it manually to the grub..

---

### Post by M4rotku on 2010-09-08
I am hesitating to do so b/c every documentation on the new grub2 system that I've read in researching this has advised against manually editing it.

---

### Post by sharathcshekhar on 2010-09-08
As you  said you want ubuntu to control Grub, you will have to reinstall grub as installing Gentoo would have over written the MBR.To Reinstall run
```

sudo grub-install /dev/sda

```
and then run update-grub.
Things should be fine.

---

### Post by M4rotku on 2010-09-08
I can try that when I get to my laptop.  But, idk if it's a problem with Gentoo overwriting stuff b/c I skipped the whole bootloader section when I was installing Gentoo.  So Gentoo hasn't tried to do anything with the grub.  However, it sounds like this could work, and I will try it when I get the chance.  Thank you for your answer!

---

### Post by M4rotku on 2010-09-08
Ok, I tried that and it didn't work.  Idk what the problem is.

---

### Post by sharathcshekhar on 2010-09-10
When you run "update-grub", can you check if Gentoo is really added to the file in /boot/grub/grub.conf?
You can open the file and check it. Something like this should be there :
```

menuentry "Gentoo, with Linux 2.6.32-14-generic (on /dev/sda2)" {
    insmod ext2
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set e5ace98f-a32d-4b4f-8c16-670be397b352
    linux /boot/vmlinuz-2.6.32-14-generic root=UUID=e5ace98f-a32d-4b4f-8c16-670be397b352 ro quiet splash
    initrd /boot/initrd.img-2.6.32-14-generic
}

```
Editing is not recommended though. Sometimes it detects the distro but does not add it if it cannot get some information. In that case you will have to manually add it, NOT by editing grub.conf, but by creating a file in a specific format mentioning about rootfs and kernel in a file placed in /etc/grub.d/40_custom
You can refer the Grub2 howtos in the earlier mentioned link as to howto create that file.

---

### Post by M4rotku on 2010-09-10
It isn't added to the file when I run the update-grub command.  I already checked that.  I guess I'll look into the information on how to add it via the method you mentioned.  thanks for your help.

---

