---
title: "need help dual booting Ubuntu and Arch linux"
date: 2011-02-12
forum: General Help
---

### Post by JoshH1000 on 2011-02-12
Ok i have ubuntu 10.10 installed on a 40gb hard drive and have setup arch linux on a seperate 160gb drive and am at the Choose bootloader screen of Arch Linux. My question is do i use arch linux to reinstall GRUB or do I choose none and configure GRUB to see both? if its the later can you tell how. Oh and Ubuntu is on sda and Arch is on sdb

---

### Post by drs305 on 2011-02-12
JoshH1000,

Greetings to the Ubuntu forums. I have not used Arch, however a quick check of the Arch wiki shows a Grub2 menuentry such as:
> 
# (0) Arch Linux
menuentry "Arch Linux" {
set root=(hd0,1)
linux /vmlinuz26 root=/dev/sda3 ro
initrd /kernel26.img
}


This is the same format as Grub 2 uses for Ubuntu, so I would recommend skipping the Arch bootloader installation. After you have Arch installed, return to Ubuntu and run "sudo update-grub". It should find Arch and add it to your normal Grub2 menu.

The only caveat is if you plan on using Arch more than Ubuntu. For ease of maintenance, I'd recommend having the controlling bootloader be the one on the system you use most. Another solution is to create a custom entry which you manually configure, although you will still have to decide which bootloader you want as the default.

---

### Post by JoshH1000 on 2011-02-12
Thank You, now GRUB loads and i see all the ubuntu w/ different kernals memtest and arch linux thank you. Also can i use BURG? i know ubuntu works with it but i don't know about Arch. UPDATE: when i select Arch from Grub which says /dev/sdb3 but then Arch looks for it on sda3  instead of sdb3. How do i tell Arch to use the other hard drive?

---

### Post by wilee-nilee on 2011-02-13
In the Ubuntu terminal. 
sudo update-grub
watch the terminal screen and see if arch shows up as being in the sdb hd.

---

### Post by JoshH1000 on 2011-02-13
> **wilee-nilee said:**
> In the Ubuntu terminal. 
sudo update-grub
watch the terminal screen and see if arch shows up as being in the sdb hd.

GRUB finds it on sdb3 but then when i boot Arch I get: Waiting 10 Seconds for device /dev/sda3
Root Device '/dev/sda3' doesn't exist Attempting to creat it. 
it should be looking for sdb3 but it looks for sda3.

---

### Post by drs305 on 2011-02-13
> **JoshH1000 said:**
> GRUB finds it on sdb3 but then when i boot Arch I get: Waiting 10 Seconds for device /dev/sda3
Root Device '/dev/sda3' doesn't exist Attempting to creat it. 
it should be looking for sdb3 but it looks for sda3.

When you say you 'boot Arch', do you mean when you select it from the Ubuntu Grub2 menu?  If so:

For *testing*, you could try editing /boot/grub/grub.cfg. Find the Arch menuentry and change any UUID to the correct value (you can get that with "sudo blkid") and change any reference to /dev/sda3 to /dev/sdb3.

Save the file and do NOT update-grub. This is a temporary edit and will be wiped out the next time update-grub is run.

If it works the next time you reboot, you can copy the entire Arch menuentry and paste it below the existing lines in /etc/grub.d/40_custom. 
Once you have saved the file run "sudo update-grub" to incorporate the custom menu into the Grub2 menu. It will appear as the last entry in the list.

I don't know why G2 isn't finding the correct device, but a custom entry would provide a bootable workaroun.

---

### Post by JoshH1000 on 2011-02-13
Its working now! somehow the id thing was wrong and the root filesystem was wrong to Thanks!

---

