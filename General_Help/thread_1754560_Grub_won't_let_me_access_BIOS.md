---
title: "Grub won't let me access BIOS"
date: 2011-05-10
forum: General Help
---

### Post by keayz on 2011-05-10
I need to change the boot order in the BIOS of my Toshiba Tecra, as I want to try loading the latest distribution from an iso disc, but Grub won't let me. As soon as the startup splash screen disappears I've tried pressing F1, Del, and Esc but all I get is the Grub startup menu. I can access a command prompt, is there any way I can get from there to the BIOS?

---

### Post by sikander3786 on 2011-05-10
Grub has nothing to do with the Bios key. Grub actually starts loading once you get past Bios. There is a sequence of keys to press for Toshiba I think.

This is what I found on the web.

> 1. Power up computer from off condition with ESC key depressed. Unit will display "Check system. Then press (F1) key"
2. Release the ESC key, press the F1 key. This will put the unit into the BIOS setup screen.

---

### Post by 3 frags left on 2011-05-10
This may sound kinda stupid, but aren't you pressing the wrong button? :P The "Select Disk" button is usually F8 or F12, and it loads waaay before GRUB appears.

---

### Post by antaios256 on 2011-05-10
> **3 frags left said:**
> This may sound kinda stupid, but aren't you pressing the wrong button? :P The "Select Disk" button is usually F8 or F12, and it loads waaay before GRUB appears.
Not a stupid question at all. Different manufacturers and even different models require a separate key set. for example HP dv7 laptops require escape key then f9 (this takes you to manually select boot device)or f1 (after escape) to get into bios

---

### Post by keayz on 2011-05-11
Thank you sikander3786 it worked and I can now try Natty.

---

### Post by keayz on 2011-05-11
Oh no it doesn't!
I can now access the BIOS and have changed the boot order to start from the CD-ROM but it still boots into Grub even though I saved the changes.
Is this a BIOS or Grub problem? Any ideas?

---

### Post by WorMzy on 2011-05-11
If you've told your BIOS to boot from CD first, and it's still showing grub, then it's either a BIOS problem, or the disk isn't bootable.

---

### Post by sikander3786 on 2011-05-11
Definitely a disc or the disc driver problem in my opinion as mentioned by WorMzy. You can try with a USB drive if your Bios is capable of booting those. See here for instructions on how to create a Live Ubuntu USB using UNetbootin.

[http://ubuntu4beginners.blogspot.com/2011/01/create-ubuntu-live-usb-using-unetbootin.html](http://ubuntu4beginners.blogspot.com/2011/01/create-ubuntu-live-usb-using-unetbootin.html)

---

### Post by drs305 on 2011-05-11
Try a different bootable CD/DVD (movie, another installation CD, etc), just to see if it will load. That is probably the easiest way to determine if it's the Ubuntu CD problem or a BIOS/hardware issue.

---

### Post by keayz on 2011-05-12
Thank you everybody for your suggestions. The BIOS is set to boot from CD-ROM first. My laptop won't boot from USB and I've tried different CDs, including the Toshiba Recovery disc, but it just loads Grub each time, though the CD does spin for a while first but then it stops while Grub boots. So I'm no further. I shall post a query on the Toshiba forum and see what they say but would still value any other suggestions.

---

### Post by Allavona on 2011-05-12
Most new Toshiba's have a "smart-optical drive" which basically means: Pain in the A@# drive. Insert your iso disc, close the tray and completely powerdown. Wait a solid minute. Hold down the "c" on your keyboard and turn on the power. On most Toshibas this will force the boot from a cd/dvd drive.

You could also try tapping the heck out of the F12 at startup  to manually select the boot device. But this entirely depends on what model Tecra you have. Phoenix BIOS usually use F12.

Finally, with Phoenix, you have to insert the flash drive into the USB port, then start-up and go into the BIOS. It will then be listed as its name (I.E. Kingston Data Traveller, HP View125, etc..) and available for use as a start device. Change the settings to boot from the USB, save and exit, and you should then boot from USB. Keep in mind that some BIOS revert back to the internal HDD at reboot if the USB device isn't present at boot, meaning to boot from USB again you gotta go through all the steps.

---

### Post by keayz on 2011-05-13
Thank you, Allavona, for your suggestions. I have tried them all and still no success. Pressing and holding 'c' does start the CD ROM drive whirring but it soon stops and reverts to Grub. Holding 'Esc' gets me into the BIOS and it is set to boot from the CD drive. F12 produced icons of the different drives and allowed me to select the boot order (no USB there though) but even though I selected the CD it still went to Grub. I'm lost.

---

### Post by sikander3786 on 2011-05-13
Are you sure your CD ROM drive is healthy? When was the last time you successfully accessed a disc using that?

If possible, can you replace the drive and try again?

But I am more than sure that this issue has nothing to do with Grub or Bios. It is just a hardware failure in my opinion.

---

### Post by patmagee1024 on 2011-05-13
Definitely a hardware problem.

---

### Post by keayz on 2011-05-14
Thank you everyone, I shall try replacing the CD drive. My apologies to Grub if I have maligned it.

---

### Post by wilee-nilee on 2011-05-14
> **keayz said:**
> Thank you everyone, I shall try replacing the CD drive. My apologies to Grub if I have maligned it.

It will get over it.;)

---

