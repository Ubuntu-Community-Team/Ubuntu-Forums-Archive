---
title: "Grub 21 Error"
date: 2010-09-19
forum: General Help
---

### Post by HalfbakedFlunky on 2010-09-19
Hi, I just want to say first off I am still very new to linux and just joined this forum. My problem is I just recently installed ubuntu v10.04 on an a 2.5" external HDD that is connected to my PC via USB. Problem is after installing it I am no longer able to access my internal HDD (Windows Vista Ultimate). If I try to boot up my PC without the external connected I get a Grub 21 error. And if I try to boot up Windows with the external HDD connected I get a Disk Read Error. The internal HDD is still being recognized in the BIOS so I don't know what to do, (as well I can access the contents of the drive when I boot up Ubuntu). Also when I try to use the reinstall disk for Vista I get the blue screen of death. I really hope I am not going to have to reformat the internal HDD.

---

### Post by dcstar on 2010-09-19
> **HalfbakedFlunky said:**
> Hi, I just want to say first off I am still very new to linux and just joined this forum. My problem is I just recently installed ubuntu v10.04 on an a 2.5" external HDD that is connected to my PC via USB. Problem is after installing it I am no longer able to access my internal HDD (Windows Vista Ultimate). If I try to boot up my PC without the external connected I get a Grub 21 error. And if I try to boot up Windows with the external HDD connected I get a Disk Read Error. The internal HDD is still being recognized in the BIOS so I don't know what to do, (as well I can access the contents of the drive when I boot up Ubuntu). Also when I try to use the reinstall disk for Vista I get the blue screen of death. I really hope I am not going to have to reformat the internal HDD.

The Grub bootloader requires a Linux system to function.

Either resize the Windows partition to make ~10GB of space to install Linux, or reinstall the Windows bootloader on the hard disk.

Do a web search for detailed instructions on both options.

---

### Post by Rubi1200 on 2010-09-19
You can find instructions for reinstalling bootloaders here:
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

### Post by Dustin2128 on 2010-09-19
> **HalfbakedFlunky said:**
> Hi, I just want to say first off I am still very new to linux and just joined this forum. My problem is I just recently installed ubuntu v10.04 on an a 2.5" external HDD that is connected to my PC via USB. Problem is after installing it I am no longer able to access my internal HDD (Windows Vista Ultimate). If I try to boot up my PC without the external connected I get a Grub 21 error. And if I try to boot up Windows with the external HDD connected I get a Disk Read Error. The internal HDD is still being recognized in the BIOS so I don't know what to do, (as well I can access the contents of the drive when I boot up Ubuntu). Also when I try to use the reinstall disk for Vista I get the blue screen of death. I really hope I am not going to have to reformat the internal HDD.
It should be fairly easy to save your data. When you boot to ubuntu you should have the option in nautilus to mount XXGB filesystem, and that'll be your NTFS (windows) partition. 

     Once you've got all your windows data saved, what I would do is detach your external drive, then use your ubuntu disk to install it to the internal HDD. Not necessarily a big partition, 6-10GB should do the trick. Once its installed, run the command:
```
sudo update-grub
```after that's done, reboot. You should have a grub list including windows. 

I'd recommend having your ubuntu dual boot on the internal drive anyway, USB 2.0 is a rather slow interface to be running your computer from.

---

### Post by HalfbakedFlunky on 2010-09-19
Problem solved. Thanks a lot for all the help everyone. Much appreciated :)

---

### Post by Rubi1200 on 2010-09-19
Glad it worked out for you :)

---

