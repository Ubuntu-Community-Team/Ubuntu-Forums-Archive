---
title: "Back Up Live USB"
date: 2011-06-03
forum: General Help
---

### Post by Dave_L on 2011-06-03
I have a Live USB flash drive that I made from ubuntu-10.04-netbook-i386.iso with Startup Disk Creator.

If I want to back up the flash drive onto a hard disk, can I do so by simply copying the files, for example "cp -a ..." or "tar ..."?

Or would I need to use "dd" or another method?

The purpose of the backup is so that I can use the flash drive for another purpose, but easily restore it back to a bootable Live USB, if needed at a later time, without having to use Startup Disk Creator.

---

### Post by linkageless on 2011-06-03
I've not tried it but I would use dd, as you would need the boot sector as well as the files therein.

---

### Post by Dave_L on 2011-06-06
Thanks.

Is "dd" the preferred method for doing this? Is there anything on the flash drive that "dd" does **not** copy?

---

### Post by linkageless on 2011-06-07
> **Dave_L said:**
> 
Is "dd" the preferred method for doing this? Is there anything on the flash drive that "dd" does **not** copy?

dd is a powerful and versatile tool, but potentially dangerous. In my book it would be the preferred method for preserving an exact copy with minimal fuss, but I use it daily as part of my job. In other words, be sure you are using the right syntax.

If you dd from the flash drive device itself (eg 'dd if=/dev/sdc of=/tmp/flashbackup.dd') then you will get everything stored therein, including deleted file fragments, any filesystem corruption, etc. It should be an exact copy from the start to the end including the boot sector. To restore it you do the copy in the other direction from your file. Simple.

Be aware that this isn't necessarily the most space efficient way of doing this. Compressing your image is an idea, or taking a dd backup of just the boot sector and doing a tar -cj of the rest might be better. There are many other ways to do this. Personally, I'd fill the unused space with a file made from /dev/zero, delete it, then once unmounted you'll get better compression on your dd image.

---

### Post by Dave_L on 2011-06-09
Thanks for the explanation. I understand that "dd" must be used with care.

So other than the 512-byte (or is it 32K) MBR, everything on the drive consists of normal files?

---

### Post by oldfred on 2011-06-09
Anther alternative.

Use the flash with grub2 and loopmount ISO files. Then it is just a copy of an ISO file (not install) to a flash drive. The tricky part is getting the correct boot stanza into grub.cfg as you have to manually create it. You can use extra space for storage even with the ISO on the flash drive if you want. I have several ISO on one flash. 

This is a script to install many ISOs. Some that will not loopmount by installing a kernel and boot image.
MultiBootUSB - Install and boot multiple Linux from Pendrive / Flash drive / USB disk 
[http://ubuntuforums.org/showthread.php?t=1518273](http://ubuntuforums.org/showthread.php?t=1518273)
[http://blog.p-mt.net/archives/644](http://blog.p-mt.net/archives/644)
MultiSystem Another LiveUSB Multiboot
[http://liveusb.info/dotclear/](http://liveusb.info/dotclear/)

I did it manually before I found the above scripts:
MultiBoot USB with Grub2 (boot directly from iso files)
Basically you just install grub2, create a folder for the isos and edit a grub.cfg to loop mount the isos.
HOWTO: Booting LiveCD ISOs from USB flash drive with Grub2
[http://ubuntuforums.org/showthread.php?t=1288604](http://ubuntuforums.org/showthread.php?t=1288604)
[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1535864](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1535864)
Install grub2 to USB -general info
[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB](http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB)

---

### Post by linkageless on 2011-06-20
> **Dave_L said:**
> So other than the 512-byte (or is it 32K) MBR, everything on the drive consists of normal files?

I've not verified this as I don't have a live usb created, but I can't imagine there can be any other 'magic' to it if it's to work with commodity hardware.

A dd of the entire device will capture it all for sure, anything else needs additional thought/checking in my book.

BTW, Nice suggestion oldfred - I'll have to remember that's one of the possibilities that grub2 opens up.

---

### Post by Dave_L on 2011-06-27
oldfred:

Thanks for the information about multibooting.  Using the MultiBootUSB script, I made a flash drive that boots SystemRescueCD, Clonezilla and Ubuntu 11.04.

linkageless:

Thanks.

---

