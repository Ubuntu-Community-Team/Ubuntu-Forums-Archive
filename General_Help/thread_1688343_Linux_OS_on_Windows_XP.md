---
title: "Linux OS on Windows XP"
date: 2011-02-15
forum: General Help
---

### Post by Michael_Grumbach on 2011-02-15
I need to load and test an application which is to be run on a Linux system.
Can Ubuntu allow me to do this on my Dell pc with Windows XP OS?

Someone suggested Ubuntu, but I want to be sure that it's not going to replace or affect the Windows XP OS.

---

### Post by adeee on 2011-02-15
> **Michael_Grumbach said:**
> I need to load and test an application which is to be run on a Linux system.
Can Ubuntu allow me to do this on my Dell pc with Windows XP OS?

Someone suggested Ubuntu, but I want to be sure that it's not going to replace or affect the Windows XP OS.

Welcome to linux world.


yes you can install ubuntu inside Windows XP OS as a application via [wubi(windows based ubuntu installer).]("http://www.ubuntu.com/desktop/get-ubuntu/windows-installer")

After that you can remove it as you remove or uninstall the other software's or other windoows applications.. its not bothered you. i bet. :P

---

### Post by ReadyFreddy on 2011-02-15
Another way you could do this, is download the latest version of Ubuntu and burn a live DVD to work from.  You can boot right from the dvd. (just don't click install)

You can also download VirtualBox and run that live dvd right in Windows.

And last but not least, you can install and run Ubuntu on a UBS drive. All these instructions can be found right on the download page of ubuntu.

---

### Post by Michael_Grumbach on 2011-02-15
Thank you both very much.

---

### Post by 3Miro on 2011-02-15
To summarize the options:

Virtual Box: this runs a copy of Ubuntu within windows. It will be much slower and you will not be able to run fancy graphics, however, it will have minimal impact on your system. You will not have to reboot to use Ubuntu.

LiveCD: you can boot from the CD and use Ubuntu without ever touching your HDD. It will be slower then running from the HDD and you will not be able to save any files, but this will have no impact on the rest of the system. You have to reboot your machine every time you want to use Linux.

LiveUSB: make a USB drive with Ubuntu. It is a lot like the LiveCD, except it is a bit faster and you can save/load data to the USB.

Wubi Install: install Ubuntu within Windows. You will have to reboot every time you want to use Ubuntu, but if you want to remove it, you can just select Uninstall from the Windows Control Panel. This will be much faster than any of the above options, however, still not as fast it can be. Also, Ubuntu will be susceptible to some windows malware (viruses and such).

Dual Boot Install: this is the hardest setup since it involves repartitioning you HDD (if you go that road, FIRST BACKUP ALL DATA on your HDD). Ubuntu and Windows will live side by side and you will be able to get full advantage of Linux speed and security.

Ubuntu Standalone: backup everything from Windows and tell Ubuntu to wipe the entire HDD and take over. This gives you full advantage of speed and security and it is one of easiest setups. You can then install Windows within Virtual Box, that is, if you still need to use it (check the Virtual Box section).

Search the forum for tutorials on all of those options. You will find plenty.

---

### Post by Michael_Grumbach on 2011-02-16
Thank you for the thorough information.
I really appreciate it.

---

