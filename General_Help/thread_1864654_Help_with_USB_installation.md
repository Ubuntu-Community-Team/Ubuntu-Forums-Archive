---
title: "Help with USB installation"
date: 2011-10-19
forum: General Help
---

### Post by hansen85 on 2011-10-19
Hi,
   I&#8217;m trying to install Lubuntu on a atom processor based computer[SIZE=2]**(Intel® Desktop Board D425KT**[/SIZE] )with 8gb usb flash pen drive and no hardisk.
Is it possible to do so ?.
I don't want to create a live version  but an installed version how can i do that?

I am able to install lubuntu  on the flash drive using a bootable CD but it wont boot from the flash drive on restart.
I have also enabled boot from flash in bios but this would help either.?

Any  help would be appreciated much.

Thanks,
Hansen

---

### Post by searchfgold6789 on 2011-10-19
If you create a Live USB with persistence enabled ("Save files and settings in allocated space...") It will be just like a full installation, and if you remove the USB disk from the computer at a later date it won't affect the existing boot options on the computer at all.
If USB boot is enabled, you may have to (rather than enter setup/BIOS) choose the device you want to boot from when your computer starts up. For my computer, say, I would have to press F12 and then select "USB Flash Drive". If your computer has such a menu you can try using that.

---

### Post by hansen85 on 2011-10-20
Hi,
  Thanks for your response I was able to create the bootable version of lubuntu by changing the usb drive.I have identical USB drives which are new and bought from HP.It works on one drive and does'nt on the other.I scanned the problematic drive with chkdsk but it found no errors.
When I boot I get an option asking me if i want to evaluate lubuntu instead  can I have an installation of lubuntu on the USB drive similar to a regular installation on the hardisk and have booting capability also?

Are there known issues of having OS run from USB drive due to the flash USB having limited write operations?

Does the OS do frequent paging and other operation in the background and write data to USB regularly?If so can I prevent this by having lubuntu to load into ram?

Regards,
Hansen

---

