---
title: "Boot from SD Card Fails"
date: 2011-12-16
forum: General Help
---

### Post by Sherifawzi on 2011-12-16
Hello,
 
I am trying to boot an HP Laptop with no Hard Disk from an Ubuntu 11.04 SD startup disk, but i always get the following error:
 
[COLOR=black][FONT=Verdana](initramfs) Unable to find a medium containing a live file system[/FONT][/COLOR]
 
If i create an image on a normal USD stick it works fine, but on an SD card i always get this error.
 
Booting from a Live CD works fine too.
 
Anyone have a clue what i am doing wrong ? and how to boot from the SD
 
Thanks
Sherif
 
P.S: SD card is setup as the first choice in the boot sequence in BIOS.

---

### Post by mikedrz on 2012-01-14
Same Issue here.. hangs at "unable to find a medium containing a live file system" 

I used Pendrive Linux to create the SD card... used various flavors of Ubuntu with same result.

it does boot fine off Live CD..

Update : Used Pendrive utility to create usb stick from same iso .. and it boots fine.

---

### Post by satanselbow on 2012-01-14
I have never seen a machine that will boot from SD. My last laptop (Compaq CQ61) even listed it in the boot options but could not be made to boot - and believe me I tried with both linux & windows tools :(

Not tried my current machine (only had it a week) - will try it tomorrow and let you know :popcorn:

edit - some useful looking info here: [http://chdk.wikia.com/wiki/Bootable_SD_card](http://chdk.wikia.com/wiki/Bootable_SD_card)

---

### Post by bluexrider on 2012-01-14
Format the SD card to FAT16 or FAT 32 make sure you remove other folders such as DCIM and MISC

Use whatever method to install the bootfiles to the SD Card as you would a USB thumbdrive and you should be set.

---

### Post by C.S.Cameron on 2012-01-15
My ol' EEE 7" boots from SD card just fine.
My 6 year old Asus u-built laptops BIOS does not see SD's, or at least it's card reader.
I think it depends on the machines BIOS.

---

### Post by gandaran on 2012-01-15
insert the SD card on a usb card reader then you can boot from the SD as a normal usb drive, very few laptops can really boot from SD cards, yours may be the case.

---

