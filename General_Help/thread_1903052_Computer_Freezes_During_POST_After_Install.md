---
title: "Computer Freezes During POST After Install"
date: 2012-01-01
forum: General Help
---

### Post by trombley2009@comcast.net on 2012-01-01
Hello All.
Happy New Year.
I just installed Ubuntu Studio 11.10 (Oneiric Ocelot) on my system.
The install seemed to work, but after the install the computer freezes during the POST.
I can't boot from any drive, HD or optical, when the hard drive I installed Ubuntu is plugged in.
GRUB does not load.  Only the power on POST screen is visible.
If I unplug the drive my computer boots fine.
I tried unplugging the drive and setting the DVD drive as the only boot drive.
This did not work.
I tried the hard drive on 2 different computers, same result.
I also tried to install Ubuntu Studio on another drive and the same thing happened.
While booting the comouter I noticed the HD activity light lights during POST then the computer freezes.
My Computer is configured with:
  Intel D865PERL motherboard with latest BIOS
 4 GB RAM
 Boot HD is an IDE drive 500 GB
    /boot and / are formatted with EXT3
    There is one /swap parition on the boot drive (4 GB)

---

### Post by Synoc on 2012-01-01
so you installed the drive, it worked fine, then you installed Ubuntu and it didn't? If you go into your BIOS settings can you tell your PC to load from CD first? just to see if you can GET something else to load?

---

### Post by trombley2009@comcast.net on 2012-01-02
When the drive is plugged in, I can't go to the bios.  I unplugged the drive and set the DVD as the only bootable drive.  This did not work.  This happened on 2 separate drives.

---

### Post by teh603 on 2012-01-02
[http://www.intel.com/support/motherboards/desktop/sb/cs-010254.htm](http://www.intel.com/support/motherboards/desktop/sb/cs-010254.htm)

Try some of the troubleshooting tips there, like clearing the CMOS memory. There's also the possibility of a bad BIOS flash; I've heard more horror stories about people bricking their computer or worse after a BIOS flash went bad, than stories of people successfully flashing. Its why I never mess with my BIOS even if its got some quirks like the old Acer Aspire One ZG5 card reader issue.

---

### Post by trombley2009@comcast.net on 2012-01-02
I reset the BIOS by setting the jumper on the board.
I did not flash the bios before I installed Ubuntu Studio.

---

### Post by trombley2009@comcast.net on 2012-01-02
I also unplugged the drive, set the DVD as the only boot drive and then replugged the drive back in.  This did not work.  I also unplugged all other drives from the PC and this did not work.  Does Ubuntu corrupt the drive firmware somehow?  If I unplug the drive my computer boots normally.  I also disconnected all of my DIMMs and tried to use the drive.  This did not work either.

---

### Post by chipbuster on 2012-01-02
That is bizzare o.0"

You say it can boot if you unplug the drive. Are you running your drives under AHCI? If so, if you boot and then plug it back in while it's running, can the computer see the device at all? Does it cause a crash?

Also, if you still have the media/original install file, did you check the MD5 sum?

---

### Post by trombley2009@comcast.net on 2012-01-03
My comptuer does not have hot swapable hardware inside.
Unfortunately I did not check the MD5 sum of the ISO before I birned/installed the OS.
I bought a new HD and will install the distro I was using before I tried Ubuntu then I will check the MD5 sum of the ISO.
I probaly should have checked the ISO before burning and installing the OS.
Now I have 2 HDs that are not usable.

---

### Post by mmjrules on 2012-03-11
Hi, I'm having the same problem after installing Xubuntu 10.10 on an old computer. At first I thought it was the disk. I installed in a new hdd and got the same results.  Does anyone know what might be wrong or how to fix it?

---

