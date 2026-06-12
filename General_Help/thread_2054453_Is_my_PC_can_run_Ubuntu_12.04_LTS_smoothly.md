---
title: "Is my PC can run Ubuntu 12.04 LTS smoothly?"
date: 2012-09-07
forum: General Help
---

### Post by JupiterFB135 on 2012-09-07
[FONT="Comic Sans MS"][SIZE="3"][/SIZE][/FONT]
I am new in using Ubuntu OS so i'm just going to ask if my PC can run the said OS.

My PC Specs:

ASUS P4P800-SE MoBo
Intel Pentium 4 3.0GHz
2.5GB Kingston DDR400
120GB Seagate Barracuda  7200.7 RPM
ATI Radeon 9600PRO Graphics Card

thus my PC can run Ubuntu 12.04 LTS?

Advanced thank you for all of you.

---

### Post by oldfred on 2012-09-07
It should.

My system is from 2006 and has the slightly newer core duo with 4GB of RAM. I have a nVidia 9600GT.
 I also run/ran 10.10 on my 2006 laptop with only 1.5GB. I have tested 12.04 but not for an extended test nor install on that yet.

[https://help.ubuntu.com/12.04/installation-guide/amd64/minimum-hardware-reqts.html](https://help.ubuntu.com/12.04/installation-guide/amd64/minimum-hardware-reqts.html)

With nVidia you will need the nomodeset boot parameter on the liveCD or USB  and on first boot if you do not install the proprietary drivers as part of the install.

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

I had to do this with my Nvidia 9600GT:
To install Ubuntu, boot from the cd press any key at accessibility circle and keyboard, press F6 and then select the nomodeset option.
USB boot - At the menu press tab on the first option to edit the boot options and replaced the 'splash' option with 'nomodeset'. 
then
On first boot after install, press e on getting the GRUB bootloader menu. 
Hold shift from BIOS boot to get menu if only one system installed.
Using arrow keys navigate to and delete quiet and splash and type the word nomodeset in their place
Press Ctrl and X to boot (low graphics mode), install nVidia driver suggested my Ubuntu

---

### Post by TheFu on 2012-09-07
With a Pentium4, I'd load either Lubuntu or Xubuntu instead of the base Unity version. Those versions require less resources.  I know that Lubuntu works nice on a Pentium4.

---

### Post by offgridguy on 2012-09-07
You should have no problem running ubuntu,  Do you already have an operating system on
your computer ie; windows?

---

### Post by JupiterFB135 on 2012-09-08
> **TheFu said:**
> With a Pentium4, I'd load either Lubuntu or Xubuntu instead of the base Unity version. Those versions require less resources.  I know that Lubuntu works nice on a Pentium4.

Thanks gonna try that 1 .

---

### Post by JupiterFB135 on 2012-09-08
> **offgridguy said:**
> You should have no problem running ubuntu,  Do you already have an operating system on
your computer ie; windows?

Yes, i do have Windows 7 Ultimate x86.
I can run it on my system without any slowdown or any problem .

i want to install Ubuntu because of lesser virus and for File safe keeping .

---

