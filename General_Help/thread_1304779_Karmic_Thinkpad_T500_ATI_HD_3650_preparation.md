---
title: "Karmic: Thinkpad T500 ATI HD 3650 preparation"
date: 2009-10-29
forum: General Help
---

### Post by luigi_mb on 2009-10-29
System is TP 500 with 4GB of RAM, ATI Mobile Radeon HD 3650 with 256MB.

Before doing a clean install of Karmic, I would like to know if the following preparation is correct:

Access BIOS and configure the display as follows:

   - Check "Discrete"
   - Uncheck (disable) "Auto OS Switch"
   - AGP set to 128 or 256MB (not less than 32MB)

I then intend to install Karmic, and the ATI driver as suggested by Hardware Driver.

Any corrections, addditions and/or advice?

Thanks in advance for any help.

---

### Post by peng-&gt; on 2009-12-14
Yes, that's the way to go if you wan to play with the dedicated vid.

After the installation is done, enter to the X and fire up a terminal type sudo apt-get update install.

Reboot the machine.

Then get the latest vid driver from ATI website: 

[http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.2&product=2.4.2.3.25&lang=English](http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.2&product=2.4.2.3.25&lang=English) 

Before installing the new driver, you have to check if the dependencies that the driver needs are satisfied, you can check into the manual page from here:
[https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_cat911-inst.pdf](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_cat911-inst.pdf)

Please report any issues or concerns, I would like to help with the driver setup.

BTW:I just got my brand new Thinkpad T500 2081 CTO2081 a week ago.


Hopefully it helps.

Peng

Cheers!

---

