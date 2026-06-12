---
title: "Booting Ubuntu off external hard drive"
date: 2010-12-18
forum: General Help
---

### Post by Marinozai on 2010-12-18
Hello. I have an old Macbook with a 160 GB hard drive and because of the hard drive size, I would like to boot Ubuntu off an external hard drive (yes, I know that I could get a bigger hard drive, but the Macbook is my paranoid mother's not mine - I just use it). Initially, I thought it would be easy. I was going to buy an external hard drive from Western Digital, plug it into the Macbook, and install Ubutnu on it so I could have my mom's Macbook as it should be and plug in the external hdd when I wanted to use Ubuntu. here is the external hard drive I was going to use, not that this will provide anything significant: [Western Digital Passport Essential]("http://store.westerndigital.com/store/wdus/en_US/DisplayProductDetailsPage/productID.219793700/subCategory.52228200,52240800,52241000/categoryID.13094100/parid.13092300/catid.13093000")

Anyway, I saw a bunch of stuff abotu how it isn't that easy and there is more to it then just installing it on the Mac and pllugging it into the Macbook and booting off of the external hard drive. Help?

---

### Post by unplugged23 on 2010-12-18
Well, as far as I know, MAC OSX runs the ubuntu live cd just fine, so you should at least be able to run the live environment from the hdd. And I would imagine that if you could run the live environment installing the full fledged system to the disk for persistent changes would only be a small step up. I don't have any kind of personal experience with mac, but I would suggest just testing the waters with a live cd/usb drive.

Best of luck!

---

### Post by ArinSky on 2010-12-18
The biggest problem I can see is if you're planning on removing the external, as in order for grub to work you'd need it plugged in, and once you install grub if you just unplug the drive and boot it will prolly give you a Grub Error 21 message. You might consider looking into a different boot manager or getting grub onto the main disk (easiest way is making a tiny ubuntu "boot os" on the main disk that takes up as little space as possible. I have a seperate one too, I also use mine to back up all of my operating systems in case something happens)

---

### Post by Marinozai on 2010-12-18
> **ArinSky said:**
> The biggest problem I can see is if you're planning on removing the external, as in order for grub to work you'd need it plugged in, and once you install grub if you just unplug the drive and boot it will prolly give you a Grub Error 21 message. You might consider looking into a different boot manager or getting grub onto the main disk (easiest way is making a tiny ubuntu "boot os" on the main disk that takes up as little space as possible. I have a seperate one too, I also use mine to back up all of my operating systems in case something happens)

Oh, I thought that I could solve the Grub problem by installing the bootloader on the external drive only.

---

### Post by efflandt on 2010-12-18
I am not familiar with Macbook, but I do have several WD Passports that work fine for booting Ubuntu on PC's.  You just need to make sure that you put grub on the USB drive and do whatever you need to do with the Macboot to boot from that when you want to.  For some computers even if you change drive order to boot USB before internal, you may still have to press a specific key during BIOS splash screen to boot USB.

For Maverick the selection during install where to put grub is at the **bottom of the manual partitioning screen**, and you probably need to use that screen anyway to put Ubuntu on the external drive.

While USB 2.0 is not that fast, the WD Passport is as fast as the 4200 RPM drive in my old laptop, and faster than all but the best expensive USB sticks (which are not any faster).

---

### Post by Marinozai on 2010-12-18
> **efflandt said:**
> I am not familiar with Macbook, but I do have several WD Passports that work fine for booting Ubuntu on PC's.  You just need to make sure that you put grub on the USB drive and do whatever you need to do with the Macboot to boot from that when you want to.  For some computers even if you change drive order to boot USB before internal, you may still have to press a specific key during BIOS splash screen to boot USB.

For Maverick the selection during install where to put grub is at the **bottom of the manual partitioning screen**, and you probably need to use that screen anyway to put Ubuntu on the external drive.

While USB 2.0 is not that fast, the WD Passport is as fast as the 4200 RPM drive in my old laptop, and faster than all but the best expensive USB sticks (which are not any faster).

Thanks for clarifying. My friend is going to give me her old WD Passport, but for now I have Ubuntu installed on this 16 GB usb drive and it's working great. Thank you!

---

### Post by Marinozai on 2010-12-19
Update - it wouldn't work. I had the external hard drive with Ubuntu installed on it. It booted of a PC fine, but when I turned on the Mac and hit option, the external hard drive didn't show up.

---

