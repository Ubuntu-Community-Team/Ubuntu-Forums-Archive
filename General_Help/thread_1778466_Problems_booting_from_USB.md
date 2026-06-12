---
title: "Problems booting from USB"
date: 2011-06-09
forum: General Help
---

### Post by subadra on 2011-06-09
I am a newcomer to Linux in general and Ubuntu in specific - brought here by total frustration with Windows 7 (and before that Vista). I wanted to have a look at Linux as an alternative and thought that having a bootable USB would be a perfect first step.

I downloaded the Universal USB Installer (version 1.8.5.2) to a Windows XP PC. I also downloaded the latest Ubuntu (Ubuntu-11.04-desktop-i386.iso).

Using the installer, and selecting Ubuntu 11.04 and selecting the installer to reformat my USB drive, everything installed without glitches.

I rebooted my PC, selected F12 for boot options and then selected USB. I then get an error message:
"No DEFAULT or UI configuration directive found. Error no configuration file found"

I have tried various things suggested elsewhere. These include:
1) Renaming the isolinux.cfg file to syslinux.cfg - made no difference
2) Editing the syslinux file removing the ui at the start of the last line
3) Reinstalling to the USB and selecting unlisted Linux iso (both old and new syslinux) - made no difference
4) Trying the USB stick in another Windows XP PC  and in a Windows XP laptop - made no difference
5) Downloading the iso agaiin and reinstalling - made no difference

My syslinux.cfg file currently contains the following:

# D-I config version 2.0
include menu.cfg
default vesamenu.c32
prompt 0
timeout 50
ui gfxboot bootlogo

Could anyone tell me what to do to get the USB to boot please?

Many thanks for any help you can give.

Duncan

---

### Post by linuxinstalledfromhdd on 2011-06-09
Well the first thing I would do is try using Ubuntu 10.10 iso. 32-bit sounds good too. :) 

[http://cinderbox.net/2010/12/23/to-do-list-after-installing-ubuntu-10-10-aka-maverick-meerkat/](http://cinderbox.net/2010/12/23/to-do-list-after-installing-ubuntu-10-10-aka-maverick-meerkat/)

Then I would use the instructions on this page (option number two)

[http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download)

You may have better results with 10.10.

---

### Post by subadra on 2011-06-09
> **linuxinstalledfromhdd said:**
> Well the first thing I would do is try using Ubuntu 10.10 iso. 32-bit sounds good too. :) 

[http://cinderbox.net/2010/12/23/to-do-list-after-installing-ubuntu-10-10-aka-maverick-meerkat/](http://cinderbox.net/2010/12/23/to-do-list-after-installing-ubuntu-10-10-aka-maverick-meerkat/)

Then I would use the instructions on this page (option number two)

[http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download)

You may have better results with 10.10.

Thanks for the response. I did use the ubuntu download webpage, option 2 that you referenced. That was my initial approach. It didn't work - as detailed in my OP. 

I need to test with 11.04 because that is what we use elsewhere and I don't want to introduce compatability issues by using different versions, so trying 10.10 isn't really any use.

Do you have any suggestions for 11.04?

Thanks

Duncan

---

### Post by subadra on 2011-06-09
> **subadra said:**
> Thanks for the response. I did use the ubuntu download webpage, option 2 that you referenced. That was my initial approach. It didn't work - as detailed in my OP. 

I need to test with 11.04 because that is what we use elsewhere and I don't want to introduce compatability issues by using different versions, so trying 10.10 isn't really any use.

Do you have any suggestions for 11.04?

Thanks

Duncan


To answer my own question - should this be of interest to anyone else - I dowloaded the iso for ubuntu-10.10-netbook. Installed that on the USB erasing the previous 11.04 install, browsed to the USB and copied the syslink folder in its entirity to my hard drive. Then reinstalled ubuntu-11.04-desktop onto the USB erasing all the previous 10.10 install, then replaced the new syslink folder with the one I'd previously copied onto my harddrive. Works perfectly.

Hope this helps someone.

Duncan

---

### Post by cbecker78 on 2011-06-09
Cool.  Good job!  Look up at thread tool at the top of this thread, and select "solved" so anyone else with this problem will know this is a thread worth looking at. 

Cheers~

---

