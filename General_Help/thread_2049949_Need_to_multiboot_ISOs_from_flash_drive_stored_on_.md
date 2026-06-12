---
title: "Need to multiboot ISOs from flash drive stored on TWO partitions"
date: 2012-08-29
forum: General Help
---

### Post by nikonian on 2012-08-29
Hi there :)

I have successfully booted multiple ISO images from a flash drive with ONE SINGLE FAT32 partition, following:

[http://ubuntuforums.org/showthread.php?t=1288604](http://ubuntuforums.org/showthread.php?t=1288604)

However, I have partitioned my 16Gb flash drive into two FAT32 partitions, and "/dev/sdb1" is where grub2 was installed using:

```
 sudo grub-install --force --no-floppy --root-directory=/media/my_sdb1_mount_point /dev/sdb
```

... and so now, in /dev/sdb1 I have "boot/grub/" structure etc, and I have created a "grub.cfg" as per the guide above, tested and working, and I can boot a standard Ubuntu ISO from /dev/sdb1.

However, I wish to allow the grub2 bootloader to boot ISO images from either /dev/sdb1 partition, as it already does **OR** from /dev/sdb2 partition, and I am a tad lost. 

Here is my "grub.cfg" I created, which doesn't work. Do I need to insert modules? Chainload? Any help would be great :)


Current, non-working grub.cfg:
```

menuentry "Ubuntu 11.04 AMD64" {
set root=(hd0,0)
    set isofile="/ubuntu-11.04-desktop-amd64.iso"
 
    loopback loop $isofile 
    linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile quiet splash noprompt --
    initrd (loop)/casper/initrd.lz
}

menuentry "Ubuntu 12.04 AMD64" {
set root=(hd0,1)
    set isofile="/ubuntu-12.04-desktop-amd64.iso"
 
    loopback loop $isofile 
    linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile quiet splash noprompt --
    initrd (loop)/casper/initrd.lz
}

```

Also, I have attached a picture of how my flash drive is laid out. Thanks guys!

---

### Post by oldfred on 2012-08-29
Your entries look close. With grub2 partitions start at 1 not 0. So sdb1 is hd1,1. But when you use BIOS to boot USB flash drive that will be hd0. So first partition should be hd0,1 and second hd0,2.

I have booted ISO from several flash drives, one with a full install of Ubuntu in one partition and the iso in another. I also have booted ISO  from NTFS formated partitions. So format does not matter.

I also use grub in one drive and boot from another drive and then it gets tricky. The boot drive is always 0, and as near as I can tell the drives then go in order, but my flash drive sometimes is sdc and sometimes sde. So I often have to use the e in grub menu and adjust the hdX or drive number.

I have ISO in a sub-directory /iso and this example is booting my sdb drive from my flash which make sdb the third drive or hd2. The ISO are in partition 4 and I used gpt so I have to add the gpt partition mod. And if you really understand all that you are doing better than I. :)

```
menuentry "Ubuntu 12.04 Precise ISO 64bit" {
    set isofile="/iso/ubuntu-12.04-desktop-amd64.iso"
    insmod part_gpt
    loopback loop (hd2,4)$isofile 
    linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile nomodeset
    initrd (loop)/casper/initrd.lz
}

```

---

### Post by nikonian on 2012-08-29
> **oldfred said:**
> Your entries look close. With grub2 partitions start at 1 not 0. So sdb1 is hd1,1. But when you use BIOS to boot USB flash drive that will be hd0. So first partition should be hd0,1 and second hd0,2.

I have booted ISO from several flash drives, one with a full install of Ubuntu in one partition and the iso in another. I also have booted ISO  from NTFS formated partitions. So format does not matter.

I also use grub in one drive and boot from another drive and then it gets tricky. The boot drive is always 0, and as near as I can tell the drives then go in order, but my flash drive sometimes is sdc and sometimes sde. So I often have to use the e in grub menu and adjust the hdX or drive number.

I have ISO in a sub-directory /iso and this example is booting my sdb drive from my flash which make sdb the third drive or hd2. The ISO are in partition 4 and I used gpt so I have to add the gpt partition mod. And if you really understand all that you are doing better than I. :)

```
menuentry "Ubuntu 12.04 Precise ISO 64bit" {
    set isofile="/iso/ubuntu-12.04-desktop-amd64.iso"
    insmod part_gpt
    loopback loop (hd2,4)$isofile 
    linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile nomodeset
    initrd (loop)/casper/initrd.lz
}

```

Thank you for your kind help with this; this grub.cfg worked a treat:

```


menuentry "Ubuntu 11.04 AMD64" {
set root=(hd0,1)
    set isofile="/ubuntu-11.04-desktop-amd64.iso"
 
    loopback loop (hd0,1)$isofile 
    linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile quiet splash noprompt --
    initrd (loop)/casper/initrd.lz
}

menuentry "Ubuntu 12.04 AMD64" {
set root=(hd0,2)
    set isofile="/ubuntu-12.04-desktop-amd64.iso"
 
    loopback loop (hd0,2)$isofile 
    linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile quiet splash noprompt --
    initrd (loop)/casper/initrd.lz
}



```

PS: What's with the shuffling around and naming conventions in grub2? Why can't they just leave it how it was? I am confused now... lol.

---

### Post by oldfred on 2012-08-29
Glad that worked.

The naming was to change partitions from starting at 0 to starting at 1. Then when you see sda1 you know it is hd0,1. Ok a is still at 0 but that seems more consistent.

---

### Post by nikonian on 2012-08-29
> **oldfred said:**
> Glad that worked.

The naming was to change partitions from starting at 0 to starting at 1. Then when you see sda1 you know it is hd0,1. Ok a is still at 0 but that seems more consistent.

So, surely the DRIVE numbers should start at 1 also, if we're talking consistency? 

Thank you.

---

