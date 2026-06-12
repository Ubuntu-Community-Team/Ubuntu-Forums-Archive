---
title: "Linux Booting Problem"
date: 2010-12-27
forum: General Help
---

### Post by IWantFroyo on 2010-12-27
I have a laptop with Windows 7 on it, and I decided to dual boot that with Linux. I added one partition to the hard drive for Linux, and when I put the disk in I got the first ubuntu screen, then a blank screen. This is the only time I've ever had problems booting Linux. I used a USB optical drive, and my laptop model was a Toshiba Satellite T235D S1360.

---

### Post by wilee-nilee on 2010-12-27
So from a booted live Ubuntu cd or thumbdrive lets see the bootscript read out; in my signature just click on it and follow the instructions. Come back to the thread and click on the # in the reply panel this makes code tags paste all the text in between.

---

### Post by drs305 on 2010-12-27
You will have to tell us what happens when you try to boot? Which menu, if any, do you see, and what happens next - blinking cursor, black screen, etc?

From the install/LiveCD, go to this site, download the boot info script, and then post the contents of RESULTS.txt

[http://bootinfoscript.sourceforge.net]("http://bootinfoscript.sourceforge.net")

---

### Post by buddajah on 2011-01-27
i am having the same issue with my toshiba t235d-1360 laptop.

1) i used the pen drive linux installer to copy ubuntu 10.10 to a flash drive. 
2) reboot and hit F2 to set the bios to boot from usb

3) boot the flash drive - get to the splash screen.

from here weather i choose live or install you see a bunch white text about probing irq's and stuff then nothing - it either locks up or something.

how do i run a boot script if i can't get a live cd up on the system?

---

### Post by drs305 on 2011-01-27
> **buddajah said:**
> how do i run a boot script if i can't get a live cd up on the system?

Depending on your system hardware, you may need to add some kernel options to the LiveCD boot options. Here is a page which discusses how to do this:
[https://help.ubuntu.com/community/LiveCDBootOptions]("https://help.ubuntu.com/community/LiveCDBootOptions")

---

### Post by buddajah on 2011-01-29
ok so i spent the last day trying to pass every parameter and change bios settings to get this to install. i still cannot get ubuntu 10.10 to install from cd or usb drive.

but i am able to get ubuntu 10.04 to work with no issues. the problem at this point is with 10.10. some one should let them know. now i can just get the mic working i would never go back to winblows bloat ware again.

the system is a toshiba T235d-1360 laptop.
AMD Turion™ II Neo Dual-Core Processor K625
ATI® Mobility Radeon™ HD 4225 - 256MB-1405MB dynamically shared g
4GB DDR3 memory
webcam
atheros wifi bgn
Standard stereo speakers, Microphone jack (mono),Headphone jack (stereo)-(working) 

Built-in microphone ( not workin)

if you thing i should report it let me know where to?

---

### Post by drs305 on 2011-01-29
> **buddajah said:**
> if you thing i should report it let me know where to?

You can try submiting a bug report with the command "ubuntu-bug ubiquity" if you aren't given the opportunity to report the installation failure right after it occurred. 

Ubiquity is the installation program. Boot the 10.10 LiveCD to the Desktop, open a terminal (Applications, Accessories, Terminal) and then run the command. Running it from the 10.10 LiveCD will allow the bug reporting system to record your system information. Once you 'send' the report you will be taken to a stie where you can include a description of what happens when you try to install from the CD.

---

