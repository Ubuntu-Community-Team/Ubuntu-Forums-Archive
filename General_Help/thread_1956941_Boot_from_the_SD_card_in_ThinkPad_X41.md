---
title: "Boot from the SD card in ThinkPad X41"
date: 2012-04-11
forum: General Help
---

### Post by chenxinghao on 2012-04-11
My ThinkPad X41 Tablet has a 49GB HD that has Windows XP Pro Tablet installed. Due to the limited space available on the HD, I want to Ubuntu 11.10 from the SD card for which the TP X41 has a reader slot. I was able to install Ubuntu on to an 8GB SD flash memory card but the TP X41 doesn't allow me to boot from the SD device.
 
Right now I am running Ubuntu from an 8GB USB flash memory, which is is inconvenient for moving around. With SD card, I can leave the card in the reader slot and never to worry about it.
 
Has anyone sucessfully boot Ubuntu from SD card with ThinkPad X41?

---

### Post by anejo on 2012-04-12
My 8GB SD booted fine on my old Thinkpad W500. I currently use a Thinkpad T420S and it still works... in fact two weeks I installed 12.04 on this box from the SD. This is my first install with Ubuntu... having been a long time Mint user.

---

### Post by chenxinghao on 2012-04-12
I can install Ubuntu 11.10 on to an SD card via the SD reader in my TP X41T. The problem is that the X41T's boot list don't include the SD reader/port. Hence I cannot get the X41T to boot with Ubuntu on the SD card.

With your ThinkPad, are you booting the laptop from its SD reader?

I tried with a SD-to-USB reader with the SD card; my X41T recognized it and could start boot but failed due to "low speed" - I guess my SD-to-USB reader device is of a low speed type.

I am looking for a way to boot Ubuntu directly from the SD reader port in my TP X41T.

---

### Post by 2F4U on 2012-04-12
Maybe this helps:

[http://www.ehow.com/how_5886130_boot-thinkpad-sd-card.html](http://www.ehow.com/how_5886130_boot-thinkpad-sd-card.html)

From that post it seems as if the SD card is not labelled as such in the BIOS boot menu.

---

### Post by chenxinghao on 2012-04-12
Thanks for the link. I have not problem booting to Ubuntu from a USB port, via a SD reader device or not.

I want to boot from the built-in SD reader port directly. The TP X41T's bios start up device list doesn't show an option for the built-in SD reader port. And that is the problem.

---

### Post by tea for one on 2012-04-12
Do you have a boot option such as "Boot from Generic Storage Device"?

When I boot from an integrated card reader, that is the option I use.

I hope this helps.

---

### Post by chenxinghao on 2012-04-12
No such boot device option in the list.

---

### Post by cptrohn on 2012-04-12
> **chenxinghao said:**
> No such boot device option in the list.

Have you tried to update the BIOS firmware or checked to see if there is new firmware available? I also know this sounds like a silly question... but is the SD card you want to boot from actually in the memory slot?  I've run across some BIOS that won't give the option to boot from some devices unless they are connected.

---

### Post by chenxinghao on 2012-04-12
Thanks for the advice.

The SD flash memory card, installed with Ubuntu 11.10, was inserted in the built-in SD card reader in the TP X41 Tablet computer when I was trying to boot the Ubuntu. Press the F12 key doesn't show the SD reader port in the list.

In the bios, the start up list also doesn't include the SD card reader.

No, I have not updated the bios. The version is dated as 2005-7-11. I will check with Lenovo to see if there is an update.

---

### Post by chenxinghao on 2012-04-14
Checked at Lenovo.com and the update is dated 12/2006 but no SD reader port boot option either.
 
I searched Lenovo community and it all seems that there is no SD reader port boot option for the old X41 and X61 tablet laptops.
 
So I hit a dead end.
 
I purchased a Sandisk Cruzer Fit 16GB USB stick and this one is very short on the "stick" side and I am going to move Ubuntu installation on to this device. Although this device is not entirely flush (compared to an SD card) when inserted, but it is the next best option to boot Ubuntu from without a built-in hard drive.
 
Thank you all who provided inputs.

---

### Post by dwhiting on 2012-12-05
How do you get your T420s BIOS to recognize the SD card reader for booting? It doesn't show up when I press F12 at boot time.

Thanks

---

