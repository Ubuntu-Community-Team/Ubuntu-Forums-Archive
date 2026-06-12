---
title: "trying to triple boot with two drives ubuntu 9.10, windows xp and Sabayon 5.0"
date: 2009-11-06
forum: General Help
---

### Post by thorncs on 2009-11-06
I just installed Ubunu 9.10, and it works fine. My problem is that it had no trouble recognizing my windows xp installation and included it in the boot menu but I also have Sabayon 5.0 on another drive but Ubuntu doesn't recognize it and won't add it to the boot menu. I have tried manually configuring grub.d and it shows up on the menu but won't load. I get a "savedefault" is not a command error. I have tried deleting that from the entry but it says the same thing. I copied and pasted my menu.lst from Sabayon and made the proper code changes but something isn't quite right. 
menuentry "Sabayon Linux (kernel-genkernel-x86_64-2.6.31-sabayon)"{
    set root (hd1,1)
  linux /kernel-genkernel-x86_64-2.6.31-sabayon  root=/dev/ram0 ramdisk=8192 real_root=/dev/VolGroup00/LogVol00 dolvm init=/linuxrc splash=silent,theme:sabayon vga=791 console=tty1 quiet resume=swap:/dev/VolGroup00/LogVol01 real_resume=/dev/VolGroup00/LogVol01
    initrd /initramfs-genkernel-x86_64-2.6.31-sabayon
    }


menuentry "Sabayon Linux (kernel-genkernel-x86_64-2.6.31-sabayon) (safe mode)"{
   set root (hd1,1)
    kernel /kernel-genkernel-x86_64-2.6.31-sabayon root=/dev/ram0 ramdisk=8192 real_root=/dev/VolGroup00/LogVol00 dolvm init=/linuxrc console=tty1 resume=swap:/dev/VolGroup00/LogVol01 real_resume=/dev/VolGroup00/LogVol01 nox gentoo=nox acpi=off ide=nodma vga=normal
    initrd /initramfs-genkernel-x86_64-2.6.31-sabayon
    }
suggestions?

---

### Post by thorncs on 2009-11-06
Well I made some minor modifications and got rid of the savedefault error message. now it says I need to load the kernel first. I know it is still on the drive.

---

### Post by ranch hand on 2009-11-06
You could try a custom entry like this one:
```

echo "Adding Mandriva on sda10" >&2 
cat << EOF
menuentry "Mandriva on sda10" {
    set root=(hd0,10)
        linux /vmlinuz root=/dev/sda10 so quiet splash
        initrd /initrd.img
}
EOF

```
It may do the trick for you.  You will have to edit it, of coarse.

---

### Post by thorncs on 2009-11-06
Well it appears that my Sabayon system is using a file management system called lvm2. Apparently the grub2 boot loader can't boot into this.

---

### Post by ranch hand on 2009-11-06
I am not sure about that.

Check the first link in the most in my sig.  I know that herman was working on that problem.

---

### Post by thorncs on 2009-11-07
I gave up on grub2 and reinstalled grub legacy following kansasnoob's howto. Now everything works the way its supposed to.

---

### Post by ranch hand on 2009-11-07
That is good.  You should mark the thread solved (top of page under Thread Tools).

---

