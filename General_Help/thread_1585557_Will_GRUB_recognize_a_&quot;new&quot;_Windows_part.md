---
title: "Will GRUB recognize a &quot;new&quot; Windows partition"
date: 2010-09-30
forum: General Help
---

### Post by WayneL on 2010-09-30
My computer is currently dual boot: Windows 2000 on first hard drive (master) and Ubuntu 9.10 on the second hard drive (slave) using GRUB 2. Both drives are on the first IDE channel. I have a third drive with a DVD/CD drive on the second IDE channel (master and slave respectively). The only thing on this drive is my photo library, which is backed up on a server.

If I were to temporarily remove the plug for the first two drives from the mother board and plug the third hard drive and DVD drive into the first IDE channel and install Windows XP on the third hard drive from the CD ROM, I would have a functioning Windows XP computer with just the hard drive and CD/DVD drive. The system would not know of the existence of the dual-boot configuration.

Now the question: Obviously, if I plug the drives back in the way they were originally, I will not have the choice on GRUB to boot into Windows XP on the third hard drive on the second IDE channel. When running from Ubuntu, can I do a GRUB update, and will it recognise the new Windows XP drive as a bootable option in the GRUB menu?

I really don't want to take the chance of destroying my current dual-boot configuration (Win 2000/Ubuntu 9.10) by installing Windows XP on the third drive with the first two drives plugged in.

I don't really want to take the time to experiment if there's no chance that GRUB will recognise the new Windows drive. 

I know. I'm a little old-fashioned. But when all my applications work fine on both platforms with the hardware (scanners and printers) I have, why change when the performance is good (2.4 GHz P4 with 2 G RAM).

Thanks so much.
Wayne

---

### Post by Mark Phelps on 2010-09-30
> **WayneL said:**
> When running from Ubuntu, can I do a GRUB update, and will it recognise the new Windows XP drive as a bootable option in the GRUB menu?

The update-grub command runs something known as the OS prober which looks for indications of OSs.

In the case of MS Windows, it's looking for boot loader files; for XP, it looks for NTLDR, for Vista/Win7, it looks for BOOTMGR.

So, to answer your question, if the third drive is connected when you run update-grub, it WILL find the NTLDR stuff on the third drive and will add an entry to your GRUB  menu for it.

Whether or not it will work after you select it, I do not know.

---

### Post by WayneL on 2010-09-30
Thanks Mark,
That's what I thought. Well, it's worth a shot.
I'll let you know if it works.
Thanks again!
Wayne

---

### Post by WayneL on 2010-10-04
Hello Mark,
Thanks for your input on my triple-boot scenario with Windows 2000, XP and Ubuntu 9.1.

As an update and for anyone else interested:

I did unplug my first two hard disks on IDE Channel 1 (actually 0), leaving my third hard disk (just containing mostly photo files). The first two disks contained dual-boot Windows 2000 and Ubuntu 9.1 using GRUB II. 

I then plugged the third hard disk (master) with the attached DVD-ROM (slave) into the empty first IDE slot and installed Windows XP from an unused XP license I had here. I chose to keep the NTFS format on the disk, and the XP install preserved all my data besides installing XP. After all the updates were finished, I changed the computer back to the original configuration: Windows 2000/Linux dual boot on the first IDE channel and the new XP install and DVD ROM back on the second IDE channel. My computer does have the BIOS option to boot on any hard disk, so I switched to the XP disk and booted off it to make sure it worked.

Now comes the good news. I rebooted, changed the BIOS setting back to hard disk 0 and booted into GRUB 2. No XP showed up yet. When Linux booted up, I switched to StartUp Manager and updated it. It found my Windows XP. Upon saving changes on closing StartUp Manager and rebooting, Windows XP was in the GRUB list along with Ubuntu and Windows 2000.

I would think that I could have had similar results had I installed Windows Vista or Windows 7 on the third disk. I would expect the same could be done with drives running off SATA instead of my semi-antique running IDE.

Thanks for helping on this. I hope this is helpful to anyone else with a similar configuration/needs.

Wayne

---

