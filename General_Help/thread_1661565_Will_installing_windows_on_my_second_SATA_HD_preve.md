---
title: "Will installing windows on my second SATA HD prevent my computer from booting?"
date: 2011-01-06
forum: General Help
---

### Post by 0949er on 2011-01-06
Hey guys. So I think to solve a specific problem I have I am going to have to install windows as a Dual-Boot Option. My main computer (and boot partition) are on my first SATA device /dev/sda. I have a second HD /dev/sdf, which I have used "disk utility" to create 2 partitions, 250 for windows, and 750 for Linux storage.

Anyways, will installing windows via windows 7 install CD onto /dev/sdf (partition one) in any way affect my current system? I guess what I mean is that will windows some how take over my boot loader and make me auto-boot to windows?

Any input would be great :) thank you for your time.

---

### Post by MaxIBoy on 2011-01-06
Try opening your case (MAY VOID WARRANTY IF APPLICABLE) and unplugging your main HDD when you install Windows. Then, plug it back in, boot Ubuntu, and run sudo update-grub to get it to show in the boot menu. Alternately, just install Windows and then boot from a live CD and reinstall grub from there (google "grub rescue.")

---

### Post by Krytarik on 2011-01-06
> **0949er said:**
> 
Anyways, will installing windows via windows 7 install CD onto /dev/sdf (partition one) in any way affect my current system? I guess what I mean is that will windows some how take over my boot loader and make me auto-boot to windows?
IMO Windows installs its boot loader in the MBR of the drive it is installed to. Thus it would not affect your current boot options. If this turns out false, you have indeed to re-install grub to the MBR of your main drive.
[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD]("https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD")

If this does not happen -as I expect-, in order to boot into Windows through the GRUB menu, you have to do
```
sudo update-grub
```

---

### Post by 0949er on 2011-01-06
So I did as the the first guy suggested, by unplugging the first HD and this worked with some minor alterations. Upon restart (with both HD's plugged in) the bios was defaulting to boot to the Second HD, so I had to change the order to the first HD (where linux is installed)

once booted up into linux, I ran "sudo update-grub", which detected my Windows 7 Partition on /dev/sdf and now I can dual boot.

Thanks for the help and advice.

---

