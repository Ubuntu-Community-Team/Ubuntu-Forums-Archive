---
title: "Grub Deleted HELP!"
date: 2010-04-08
forum: General Help
---

### Post by czanella on 2010-04-08
Ok, Kubuntu wasnt logging in right (i just installed it) so i just assumed something disnt install right. So i went to my vista and deleted the Kubuntu partition(i forgot about grub..). I reset PC, And now im stuck at the grub loading menu.... 
"GRUB loading.
error: unknown filesystem
grub rescue>"
None of the normal commands work, Sudo is gone, Im all confused, i need chocolate....
Anyway thats not all, At first i wasnt that upset because i was thinking i could just put in my Kubuntu Cd and reload grub... But when i put a cd in my computer now i cant boot from it... My vista recovery cd wouldnt boot, nor would my Thumb drive.....
My Laptop is a TOSHIBA SATELLITE A215-S4757 (And yes ive booted both cd's before, and a Thumbdrive... But before it was a different thumbdrive[just adding it in their])
Thumb drive is a sandisk 4gb from walmart.....
Any ideas how to fix this.... im stuck here ive got a paper due tomorrow and its on this pc....

---

### Post by uRock on 2010-04-08
> **presence1960 said:**
> You can repair the MBR to a windows MBR from ubuntu or the ubuntu live CD. Install lilo by running in terminal ```
sudo apt-get install lilo
```Ignore the warning and next run in terminal ```
sudo lilo -M /dev/sdX mbr
```where is sdX is your disk/device, i.e. sda, sdb,sdc, etcThat should get you fixed up. I have used t for Windows 7 and worked flawlessly, it should do the same for you.

You can also try reinstalling kubuntu, but when you first start the disk select the test function first. It could be a bad image.

Cheers,
Ronnie

---

### Post by czanella on 2010-04-08
I cant boot in a live CD. as i said before, it wont boot either cd's. The image is good, and i know the recovery cd is good. my F12 only gives me 1 option and thats my hard drive. i wish i could use sudo and apt-get but im not even that far... I cant get anywhere farther than the "grub rescue>" is their a way to make my pc boot into a cd without f12? When i go F2 into setup, cd or thumbdrive isnt even an option, only my hardrive. its like im cursed....

---

### Post by uRock on 2010-04-08
> **czanella said:**
> I cant boot in a live CD. as i said before, it wont boot either cd's. The image is good, and i know the recovery cd is good. my F12 only gives me 1 option and thats my hard drive. i wish i could use sudo and apt-get but im not even that far... I cant get anywhere farther than the "grub rescue>" is their a way to make my pc boot into a cd without f12? When i go F2 into setup, cd or thumbdrive isnt even an option, only my hardrive. its like im cursed....

I have had that problem before with my BIOS deciding to block USB. If you have not tuned BIOS or had someone tune BIOS, then you should be able to go back into F2 and go to the last menu to the right and select restore system defaults. This should give you  control over boot order.

---

### Post by czanella on 2010-04-08
Genious! YOU ARE AMAZING. Thank you, very helpful. :)
That only took 3 hours of my life away.... a stupid default.....

---

### Post by czanella on 2010-04-08
just a random question, is their a way i could eliminate  grub entirely? can i just use the vista boot to select kubuntu?  theortically if i installed kubuntu again with grub, then restored my vista which would restore the boot to vista would i be able to still get kubuntu on?

---

### Post by uRock on 2010-04-08
> **czanella said:**
> just a random question, is their a way i could eliminate  grub entirely? can i just use the vista boot to select kubuntu?  theortically if i installed kubuntu again with grub, then restored my vista which would restore the boot to vista would i be able to still get kubuntu on?

Nope. Sorry. Not unless they are both on different hard drives and BIOS would allow you to choose which HDD to boot from.

---

