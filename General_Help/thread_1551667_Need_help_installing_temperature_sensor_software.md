---
title: "Need help installing temperature sensor software"
date: 2010-08-12
forum: General Help
---

### Post by drlemon on 2010-08-12
Hi,

I am trying to install CPU temperature monitoring software on 64-bit Lucid (e.g, XSensors). I was following these instructions: [http://news.softpedia.com/news/How-to-Install-lm-sensors-on-Ubuntu-47205.shtml]("http://news.softpedia.com/news/How-to-Install-lm-sensors-on-Ubuntu-47205.shtml"). I obtained the package lm-sensors ("aptitude show lm-sensors" shows version 1:3.1.2-2), ran "sudo sensors-detect", and at the end of the output it gives me the following:
```
Now follows a summary of the probes I have just done.
Just press ENTER to continue: 
Driver `ipmisensors':
  * ISA bus, address 0xca2
    Chip `IPMI BMC KCS' (confidence: 8)

Driver `w83795':
  * Bus `SMBus I801 adapter at 0400'
    Busdriver `i2c_i801', I2C address 0x2f
    Chip `Nuvoton W83795G/ADG' (confidence: 8)

Warning: the required module ipmisensors is not currently installed
on your system. If it is built into the kernel then it's OK.
Otherwise, check [http://www.lm-sensors.org/wiki/Devices](http://www.lm-sensors.org/wiki/Devices) for
driver availability.

Warning: the required module w83795 is not currently installed
on your system. If it is built into the kernel then it's OK.
Otherwise, check [http://www.lm-sensors.org/wiki/Devices](http://www.lm-sensors.org/wiki/Devices) for
driver availability.

No modules to load, skipping modules configuration.

Unloading i2c-dev... OK
Unloading i2c-i801... OK


```

The file /etc/modules is unchanged after running sensors-detect, the command "sensors" replies "No sensors found!", and the window of XSensors is blank.

I do not understand the information on the webpage suggested by sensors-detect [http://www.lm-sensors.org/wiki/Devices]("http://www.lm-sensors.org/wiki/Devices") . For example, regarging the 'ipmisensors' driver it gives the following:
> 
(2005-10-29) Requires an SMBus adapter supported by the i2c-i801 driver and the following kernel patches: 1)  Open IPMI 2.6 Kernel Patches for the ipmi-smb driver and asynchronous I2C transfers from Corey Minyard on a 2.6.12 kernel: linux-ipmi-2.6.12-base.diff, linux-ipmi-2.6.12-smb.diff, linux-i2c-2.6.12-nonblock.diff, linux-i2c-2.6.12-i801-nonblock.diff, and 2) The  bmcsensors/i2c-ipmi port to Linux 2.6 by Yani Ioannou: bmcsensors-26-20050808.tar.bz2

which is total gibberish to me.

Can anyone provide any help please? I am trying to put a nice Intel Xeon-powered workstation to a good use for scientific computation under Ubuntu, and I need to be sure that it is doing well with what I throw at it.

Thanks!

---

### Post by earthpigg on 2010-08-12
is the motherboard or other hardware newer (or close to as recent as) the _4_th month of 20_10_?

if the hardware didn't exist as of the 10.04 release of Ubuntu, it may not be very well supported.

is your system up to date? having the latest-and-greatest kernel may rectify this problem. or, it may not.


edit: based on that, you may want to try installing the i2c-tools and openipmi packages for the ipmisensors driver to work.

getting w83795 to work looks like it will be a bit beyond what i would give directions to without having the hardware in front of me to test myself. (i dont want to give you directions that could potentially break your install).

---

### Post by drlemon on 2010-08-12
Thanks for the reply, earthpigg!

> **earthpigg said:**
> is the motherboard or other hardware newer (or close to as recent as) the _4_th month of 20_10_?

Yes, I have a very recent motherboard, Supermicro X8DA3, and the system is up to date with kernel built July 28, 2010. I tried installing openipmi and i2c-tools and running sensors-detect again, but it still can't find the ipmisensors driver. 

I don't want to install anything on the system that doesn't come from Ubuntu repositories. So if you are correct, and my motherboard is not yet supported, I'll just have to trust that the BIOS settings for fan control will do the job of cooling the processors correctly.

---

### Post by earthpigg on 2010-08-12
I also like sticking to repos, and had similar problems with lm-sensors, and other stuff, when i first assembled my computer with bleeding edge hardware.

I used Arch while waiting for Ubuntu to catch up, but my concerns where a bit more pronounced than yours. I couldn't see what was going on with lm-sensors, ***and*** the fan sounded like it was constantly at full speed with Ubuntu 9.04. I had no idea if my CPU was constantly on the verge of melting, or what.

If your fans aren't going nuts and you aren't experiencing random lockups, you are probably safe with Ubuntu.

I was happy with Arch, so didn't try Ubuntu again until 10.04. Somewhere during that time, the correct updates had made their way from Linus Torvalds and his crew into Ubuntu.

---

