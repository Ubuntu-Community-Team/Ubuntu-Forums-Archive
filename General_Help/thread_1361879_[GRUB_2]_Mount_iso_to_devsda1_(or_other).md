---
title: "[GRUB 2] Mount iso to /dev/sda1 (or other)"
date: 2009-12-22
forum: General Help
---

### Post by BLuFeNiX on 2009-12-22
I'm trying to make grub2 boot a bitdefender rescue cd (knoppix based). During the boot up it tries to find where the cd is mounted, but fails.

here is my grub.cfg:
```

menuentry "Bitdefender Rescue CD" {

    set isofile="/boot/iso/bitdefender_rescue.iso"

    loopback loop $isofile

    set gfxpayload=1024x768x16,1024x768

    linux (loop)/boot/isolinux/linux ramdisk_size=131072 init=/etc/init lang=us apm=power-off nomce loglevel=0 quiet BOOT_IMAGE=KNOPPIX

    initrd (loop)/boot/isolinux/minirt.gz

}

```

I get a message that KNOPPIX filesystem cannot be found and it drops me to a limited shell.

how would I change grub.cfg to mount the loopback to /dev/sda1? (or any directory for that matter)

I'm also not sure about the "BOOT_IMAGE=KNOPPIX" part, but I'll fix that next.

---

### Post by BLuFeNiX on 2009-12-22
No grub experts?

---

### Post by muckblit on 2010-02-09
Is there really a /boot/isolinux? I have only ever seen /isolinux.

---

### Post by muckblit on 2010-02-09
Look in knoppix forums for kernel opts such as isoloop= isofrom= or iso-scan/filename=

They are not standardized yet. The most powerful one is ubuntu iso-scan/filename= which you can read about here in usbdrive grub2 threads.

---

### Post by Adderoll on 2010-08-29
Just in case no-one has answered this question somewhere else (im too lazy to look) the entry that worked for me in grub2 was the following:

menuentry "BitDefender" {
    loopback loop /bitdefender-rescue-cd.iso
    linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=/bitdefender-rescue-cd.iso splash --
    initrd (loop)/casper/initrd.gz
}

kthnxbye

---

### Post by drs305 on 2010-08-29
BLuFeNiX,

I've created a thread on booting ISOs from Grub 2 but have no experience with BitDefender. 

If you will confirm Adderoll's menuentry I'd like to put ut in my thread as a known working solution. The thread is:
[ISO Booting with Grub 2]("http://ubuntuforums.org/showthread.php?t=1549847")

@ adderoll,

I notice the initrd is ".gz". Are you using the most current BitDefender ISO? I don't know, I just ask because the later Ubuntu ISOs are using initrd.lz instead of initrd.gz in /casper

---

### Post by Jack Smith on 2011-02-19
> **drs305 said:**
> BLuFeNiX,

I've created a thread on booting ISOs from Grub 2 but have no experience with BitDefender. 

If you will confirm Adderoll's menuentry I'd like to put ut in my thread as a known working solution. The thread is:
[ISO Booting with Grub 2]("http://ubuntuforums.org/showthread.php?t=1549847")

@ adderoll,

I notice the initrd is ".gz". Are you using the most current BitDefender ISO? I don't know, I just ask because the later Ubuntu ISOs are using initrd.lz instead of initrd.gz in /casper

I can confirm that adderolls menuentry works.  I have bitdefender loaded on a grub2 multiboot usb drive, and it will boot.  The ISO image i used was current and it did use initrd.gz.  I did rename the ISO and took out the splash part of adderolls menuentry, i also added the $isofile variable.

The menuentry i used looks like this.

```
   menuentry "BitDefender" {
set isofile="/boot/ISO/bitdefender.iso"
loopback loop (hd0,msdos1)$isofile
linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile
initrd (loop)/casper/initrd.gz
}

```

---

### Post by drs305 on 2011-02-20
Jack, thanks for adding this.

---

