---
title: "Has anyone used my USB Install Guide with Dapper yet?"
date: 2006-04-19
forum: General Help
---

### Post by DaBruGo on 2006-04-19
Hi folks,

Has anyone used my USB Installation Guide (SUCCESS - Breezy loaded on external USB drive) to load Dapper onto a USB device?

I had someone in my thread asking about it and ... well ... I haven't tried it yet with Dapper (I know, shameful of me).

If you have gotten it to work, could you post in the [thread]("http://www.ubuntuforums.org/showthread.php?t=80811") for the benefit of those asking about it. Any tips/tricks would be great as well as any hiccups you may have dealt with.

Thanks in advance for sharing your knowledge with others.


DAVE

---

### Post by hanzomon4 on 2006-04-24
Yeah your guide worked for me

---

### Post by DaBruGo on 2006-04-24
[QUOTE=hanzomon4]Yeah your guide worked for me[/QUOTE]

That's great!

Did you have to change any of the install steps?


DAVE

---

### Post by hanzomon4 on 2006-04-26
Nope

---

### Post by bwrutter on 2006-09-22
I had loads of trouble till I realised the installer is trying to mount the Dapper partitions to /target/.... but was not correctly unmounting from /media/usbdrive. Also the format stage had trouble if the partitions were mounted before the install was run from the live CD

1) Boot with the live CD and NO USB drive
2) Install the usbdrive
3) sudo unmount all existing external disk partitions 
   if you are going to reformat the drive
4) Created the partitions needed using cfdisk.
   No need to format partitions at this stage. 
   If you do it will not be recognised by the Dapper installer anyway
   make sure to create at least 1 2Gb root (/) and a swap partition at 
   this stage
5) I had to reboot at this stage as it would not proceed without
   the live CD looking for the partitions itself. Seems to hook the old
   drive layout
   Note if you create too many partitions then the live CD will not load
   with the USB connected. It complains of not enough resources
6) Plug in USB after reboot
7) unmount the all the external partitions it auto mounts on the USB
8) run installation and select manually partition then skip past to assign
   the partitions.
9) Assign the partitions and tick the box to format every partitions


TO AVOID RESCUE REBOOT
======================
10) Do not reboot when asked
11) From a terminal mount the root and boot partitions in my case
    sudo mount /dev/sda3 /media/usbdisk               (/)
    sudo mount /dev/sda1 /media/usbdisk-1             (boot)

Now you can go directly to step 8 of the main installation and patch the modules and files. This saves booting to a rescue partition when using dapper. You will need to use chmod as appropriate

(STEP 8) in my case with mount points above.
sudo vim /media/usbdisk/etc/mkinitramfs/modules

(STEP 9)
sudo vim /media/usbdisk/etc/mkinitramfs/initramfs.conf

(STEP 10)
sudo cp /media/usbdisk-1/initrd.img-2.6.15-26-386 /media/usbdisk-1/initrd.img-2.6.15-26-386-ORIG

sudo mkinitramfs -d /media/usbdisk/etc/mkinitramfs -o /media/usbdisk-1/initrd.img-2.6.15-26-386 /media/usbdisk/lib/modules/2.6.15-26-386

(STEP 11)
No need to change grub as Dapper put in the correct drive and partitions.

NOW I simply restarted the live CD and changed the bios to look at the USB drive first and it booted.

Hope this all helps

---

### Post by Ben Cook2 on 2006-11-13
Thanks bwrutter,

Here I Was Thinking I HAD To Use The Alternate CD.
You Saved Me.

---

### Post by kaptengu on 2006-11-13
Your guide saved my day.

---

