---
title: "Boot problems"
date: 2012-06-11
forum: General Help
---

### Post by disabled20191128 on 2012-06-11
For the last 3 days i have been trying to install ubuntu 12.04 lts 32-bit on my laptop, but every time i succesfully install it, it takes a lot of time to boot. ( 3 to 5 minutes)  So i have reinstalled it over 8 times thinking it may be a bug in the installation process. Have i done anything wrong?

Specs

Acer aspire 5741G
Intel i5 430, 2 cores, 2.26GHz (although it shows me 4 cores in system monitor)
4GB of ram

(I also remember that when i had first installed Ubuntu 12.04 (some weeks ago) the boot used to take less than 30 seconds)

---

### Post by VE6EFR on 2012-06-11
It sounds like something odd is happening. Out of curiosity, are you installing from the same disc each time? Or did you install from a fresh download and burn a new install CD or usb?

---

### Post by disabled20191128 on 2012-06-11
different cds and usbs

---

### Post by ajgreeny on 2012-06-11
You can check the CD easily from the first menu that appears after choosing the language.  If it shows any errors you need to burn or download again, but check your iso file first with md5sum.
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
[https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by disabled20191128 on 2012-06-12
Help me please!

---

### Post by disabled20191128 on 2012-06-12
Could it be the hard drive?

---

### Post by disabled20191128 on 2012-06-12
Because the installs take longer than normal (2-3 hours to install ubuntu 10.04)

---

### Post by drs305 on 2012-06-12
Where is the delay occurring? (i.e. before you see the Grub menu, after you select something from the menu, after you see the Ubuntu splash screen, etc)

If it's after the Grub selection you could try installing *bootchart*, which creates a graphical depiction of the boot process and shows the amount of time it takes to run processes.

The following Ubuntu Community doc link discusses bootchart and provides 'typical' bootcharts for various Ubuntu releases:
[https://wiki.ubuntu.com/BootCharting]("https://wiki.ubuntu.com/BootCharting")

---

### Post by disabled20191128 on 2012-06-12
Well i get a black screen for about 20 seconds then a dark purple one for 1 to 2 minutes, then the Ubuntu logo (with the red dots underneath) for 30 seconds and finally the login screen that takes 15 seconds to load.

---

### Post by disabled20191128 on 2012-06-12
The system also is laggy and the dash home ( icon at the top left corner ) doesn't display anything and even if i type something in the search bar nothing shows up.

---

### Post by drs305 on 2012-06-12
At the grub menu (hold down the SHIFT key during boot if you don't normally see it), press 'e' to edit the menu item.

Cursor to the end of the 'linux' line and backspace to remove "quiet splash' and the 'vthandoff' entry. Add *nomodeset* and press F10 to boot (or ctrl-x).

Does it still take a long time to boot? If so, take a look at bootchart.

---

### Post by disabled20191128 on 2012-06-14
I actually formatted the disk, i took it out and connected it to a windows pc and with the wd disk utility i wrote zeros on the whole disk, then i put it back and it was working faster, the boot dropped from 5 minutes to 20 seconds!

---

### Post by Ashtechsmith on 2012-06-14
GRUB is a great but I prefer not to install it on my mbr., How do I chainload GRUB from Windows boot.ini, How do I chainload GRUB from Windows Vista, I have Linux in my second hard disk and I follow other howto instructions but I cannot get it to be chainloaded from Windows 

    How to boot Windows without problems., I had Linux and Windows in dual boot and then Windows no longer boots., I had both Ubuntu and Windows installed and now Windows boots just hangs., Lost my Windows boot after an Ubuntu Linux packages update 

    How to boot Windows from my second hard disk without problems., I had Linux and Windows (on my second hard disk) in dual boot and then Windows no longer boots., I had both Ubuntu and Windows installed and now Windows (on my second hard disk) boots just hangs. 

    How do I remove GRUB?, I have removed Linux partition but I see GRUB at boot and I cannot access my Windows, I am tired of Linux who do I remove that GRUB thing., How do I hide my Linux installation? 

    Can supergrub access and start the recovery partition for vista?, How do I boot my Windows recovery partition? 

    Vista does not boot after a Linux installation, winload.exe......is missing or corrupt. 

    I have deleted my Windows boot partition, I have used Windows chainloads Grub but I selected the Windows partition (my mistake!) 

    Windows refuses to boot

---

