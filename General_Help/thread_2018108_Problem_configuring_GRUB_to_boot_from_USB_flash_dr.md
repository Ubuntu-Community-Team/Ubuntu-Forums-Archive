---
title: "Problem configuring GRUB to boot from USB flash drive"
date: 2012-07-06
forum: General Help
---

### Post by cjsmall on 2012-07-06
I have an Asus U56E laptop configured to dual boot Xubuntu 12.04 and Windows 7, with GRUB2 version 1.99.

The configuration is pretty vanilla and set up so that I can properly boot into either OS from the GRUB menu.  I have created a bootable USB flash drive with Ubuntu 12.04 and when the stick is attached to a USB port, under Ubuntu it mounts the FAT32 partition as /dev/sdb1, and from the GRUB menu it is accessible as (HD1,1).

I have reviewed the instructions on the [BootFromUSB]("https://help.ubuntu.com/community/BootFromUSB") page, however I have come to the conclusion that this is written for a different version of GRUB (version 1??).  When I am at the GRUB command line, there are no "root" or "find" command which are referenced on this page.  Also, there is no /boot/grub/menu.lst file as part of my installation.  This last fact is the most telling that this documentation appears to be out of date.

So my question are:

1: Exactly what command should I be using at the GRUB command line to boot from (HD1,1)?  [Note: I tried boot (HD1,1) and that fails.]

2) Where should I be making an entry so that booting from the flash drive appears as an entry in the loader menu?

3) When I insert a bootable Ubuntu CD and reboot, GRUB automatically selects the CDROM as the boot device.  How is this being accomplished withing the GRUB configuration?  I have not yet found any documentation that explains this automatic search sequencing.

Thanks.

---

### Post by wilee-nilee on 2012-07-06
You are correct in that the link is using grub-legacy.

I think what might be helpful here is a more detailed description. 

What is installed now in the computer, and what the exact use of a usb drive is here, and exactly what is on it and your end goal.

---

### Post by cjsmall on 2012-07-06
In reply to wilee-nilee: 	 		 		> What is installed now in the computer, and what the exact use of a
> usb drive is here, and exactly what is on it and your end goal.

The original installation was Ubuntu 11.10 installed on the existing Windows 7 machine, repartitioning Windows as part of that installation.  Ubuntu was later upgraded to 12.04 and the xfce4 and other Xubuntu components were added.  The dual boot system works as expected.

I downloaded the ISO image of Ubuntu 12.04 and created a bootable CDROM and also installed this on a 2GB flash memory stick.  My purpose with the flash drive is just to have it in reserve should I ever have some sort of system failure and need to boot from other than the internal disk.  I can do this now using the CDROM, but am interested in being able to use the flash drive, first, because it would be faster, and second, because I would like to understand the GRUB boot loader better.

I have a lot of UNIX (Solaris) experience, and am now trying to bring myself up to speed on the intricacies of Linux.  I'm happy to read documentation on this issue if anyone can point me to something current that will be applicable to the current setup.

---

### Post by wilee-nilee on 2012-07-06
> **cjsmall said:**
> In reply to wilee-nilee:                       > What is installed now in the computer, and what the exact use of a
> usb drive is here, and exactly what is on it and your end goal.

The original installation was Ubuntu 11.10 installed on the existing Windows 7 machine, repartitioning Windows as part of that installation.  Ubuntu was later upgraded to 12.04 and the xfce4 and other Xubuntu components were added.  The dual boot system works as expected.

I downloaded the ISO image of Ubuntu 12.04 and created a bootable CDROM and also installed this on a 2GB flash memory stick.  My purpose with the flash drive is just to have it in reserve should I ever have some sort of system failure and need to boot from other than the internal disk.  I can do this now using the CDROM, but am interested in being able to use the flash drive, first, because it would be faster, and second, because I would like to understand the GRUB boot loader better.

I have a lot of UNIX (Solaris) experience, and am now trying to bring myself up to speed on the intricacies of Linux.  I'm happy to read documentation on this issue if anyone can point me to something current that will be applicable to the current setup.

The install on the usb is not a full install it is to small. it is a live set up.

Grub can be reloaded and completely purged and reloaded if needed, using the method you want is not optimal, a live cd on a usb is not for booting the internal with grub.

---

### Post by oldfred on 2012-07-06
If you just want to install grub2's boot loader to the MBR of the flash drive.

Install grub2 to USB -general info
[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB](http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB)


I do that to all my flash drives. But you have to manually create a grub.cfg to have any boot entries as there is no os-prober or update-grub without the full Ubuntu install.

---

### Post by cjsmall on 2012-07-07
Thanks for all the feedback so far.  I really appreciate it.  Maybe there is something that I'm not understanding, so let me explain my view of things a bit further.

What I'm really interested in is being able to boot a mini-OS in the event of some sort of internal disk drive error that keeps me from booting normally.  Then I can mount the internal drive and hopefully make repairs.

Now, as I understand things so far, GRUB2 installed its own boot loader in the MBR sector.  I assumed that this was a stand-alone, self-contained program that could perform various load operations, but now I'm confused.  It appears that the boot loader requires the config files located on the Ubuntu partition under /boot/grub, so that if this partition is corrupted, then the normal boot options will not be available.  Is this understanding correct?  If so, what action will the boot loader take under those conditions?  I assume it will still search for a bootable floppy if present, so if I insert my Ubuntu live CD, then it will boot from that.  What I was actually trying to do was be able to use the flash drive in lieu of the CD, but when it is plugged in, the boot loader does not "see" it upon boot.  I though by adding an entry to the GRUB2 configuration, I could make the flash drive be selectable during boot so that I could test out the contents and make sure that it would work similar to the way the CD boots.  However, it will not be much use in an emergency unless the MBR boot loader will find it on its own.

Does this make it clearer as to what I am interested in doing?  And does this reveal some glaring hole in my understanding of the entire boot process? :-)

---

### Post by oldfred on 2012-07-07
Grub is just a boot loader and has very limited tools. You may be able to manually boot with grub if everything else is ok, but not make any repairs.

Always best to have liveCD of the current version of every operating system you have installed to make repairs. And it does not hurt to have several repair CD or USB.

Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

If your computer boots from flash drives you can just create a bootable flash drive.

Also instructions for CD or USB
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
Write image or burn image not copy ISO as one large file to CD.
[http://www.ubuntu.com/download/help/burn-a-cd-on-windows](http://www.ubuntu.com/download/help/burn-a-cd-on-windows)
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

