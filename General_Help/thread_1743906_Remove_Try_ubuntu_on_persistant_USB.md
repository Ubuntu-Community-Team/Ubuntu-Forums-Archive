---
title: "Remove Try ubuntu on persistant USB"
date: 2011-04-29
forum: General Help
---

### Post by sml156 on 2011-04-29
Does anyone know how i can get rid of the way Ubuntu starts , I have used Linux live cd creator to install 11.04 to my 4 gig usb drive with 3 gig persistent and it has to boot up then ask's me to either try Ubuntu or install it and it seems to take forever

---

### Post by C.S.Cameron on 2011-04-30
This question comes up a lot.
A Live install using Unetbootin does not have quite as bad an opening screen.
But persistence needs to be added manually
You can also do a Full install to the flash drive, which acts just like an install to internal drive.
If you do a Full install I would recommend disabling your internal drive beforehand.

---

### Post by sml156 on 2011-04-30
I did what I believe is the easiest way to install it to a flash drive with persistent using lili usb creator . The only problem is that I have to press the shift key while it is booting to choose persistent I don't know where or how to edit the grub menu it's not in /grub anymore . I have a file called loopback.cfg 

> menuentry "Try Ubuntu without installing" {
    linux    /casper/vmlinuz  file=/cdrom/preseed/ubuntu.seed boot=casper iso-scan/filename=${iso_path} quiet splash --
    initrd    /casper/initrd.lz
}
menuentry "Install Ubuntu" {
    linux    /casper/vmlinuz  file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity iso-scan/filename=${iso_path} quiet splash --
    initrd    /casper/initrd.lz
}
menuentry "Check disc for defects" {
    linux    /casper/vmlinuz  boot=casper integrity-check iso-scan/filename=${iso_path} quiet splash --
    initrd    /casper/initrd.lz
}
menuentry "Test memory" {
    linux16    /install/mt86plus
}


---

### Post by jondodson on 2011-04-30
> **C.S.Cameron said:**
> 
You can also do a Full install to the flash drive, which acts just like an install to internal drive.
If you do a Full install I would recommend disabling your internal drive beforehand.

+1 for this.  Dunno why, but I had to unplug the Sata drive cable to all my drives before the live cd would install to the USB stick.   Reconnect the Sata cables after install and set bios boot priority to USB first and you're good to go.

---

### Post by C.S.Cameron on 2011-04-30
> **sml156 said:**
> I did what I believe is the easiest way to install it to a flash drive with persistent using lili usb creator . The only problem is that I have to press the shift key while it is booting to choose persistent I don't know where or how to edit the grub menu it's not in /grub anymore . I have a file called loopback.cfg

To automate persistence add persistent to grub.cfg as follows:


menuentry "Try Ubuntu without installing" {
linux /casper/vmlinuz file=/cdrom/preseed/ubuntu.seed boot=casper iso-scan/filename=${iso_path} quiet splash -- **persistent**
initrd /casper/initrd.lz
}

I think with lili you can do the same to loopback.cfg
with a Startup Disk creator install you modify text.cfg and with an UNetbootin install you modify syslinux.cfg.

---

