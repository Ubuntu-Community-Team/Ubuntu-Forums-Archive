---
title: "Getting desperate... Need urgent help"
date: 2011-06-07
forum: General Help
---

### Post by W33DY on 2011-06-07
Hi everyone :) recently I installed fedora that works like ubuntu I think. But I did a big mistake and now only appears this to me. What I want to do is uninstall everything and having only windows working. I have the original DVD of windows 7 ultimate with me, but it doesn't pass from here. I put the boot to the dvd drive and appears "press any key to continue...", I pressed enter and stops here eveything. What can I do so get windows working again? :S

Link to the image: [http://imageshack.us/photo/my-images/94/imagem0007a.jpg/](http://imageshack.us/photo/my-images/94/imagem0007a.jpg/)

---

### Post by seawolf167 on 2011-06-07
Enter BIOS, ensure that booting from CD/DVD is enabled and set to a priority higher than the internal hard drive. Reboot with the disk in the drive, you can also press the function key (usually [F12]) to get a one time boot menu.

Select the cd/dvd drive as the boot device, then continue as normal.

---

### Post by blueridgedog on 2011-06-07
+1 to SeaWolf's comment...set your bios to boot off of CD/DVD and install as normal.  You will need to format the drive during the install process.

Examples of the process: [http://www.hiren.info/pages/bios-boot-cdrom](http://www.hiren.info/pages/bios-boot-cdrom)

---

### Post by Frogs Hair on 2011-06-07
The Windows cd should start right up . I would check the disc with another computer if you have the option . Don't run the installation , but see if you can view the contents. Fedora has a different package system than Ubuntu , but I don't see how that would keep the Windows disc from starting.

---

### Post by ajgreeny on 2011-06-07
If you have not already done so, and I am not quite sure from your post if you have or not, I think you may need to delete the fedora partitions so that your Win7 DVD realises that there really is a hard disk to install onto.  However it looks as if grub is still starting but finding no configuration files, hence the error message, so you must chsck your BIOS for first boot device priority, which should be the CD/DVD.

Once there is a clean, empty disk the windows installation my proceed more as you expected, but at the moment, windows is not nearly clever enough to know that there is anywhere to install to, because it can not see linux filesystems.

---

### Post by W33DY on 2011-06-07
Thank you so much for all your answers. I already found a way to "fix" this. It was my keyboard --. when it appears "press any key to continue.." i pressed and nothing happened. I was using a wireless logitech keyboard. Then I went to my room and I tried with a 12 year old keyboard that still works perfectly and in that part I pressed enter and it enters on the menu :)

---

### Post by seawolf167 on 2011-06-07
Well that works too! I guess I skipped the step of "is the keyboard plugged in and working" :P

---

