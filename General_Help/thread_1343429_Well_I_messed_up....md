---
title: "Well I messed up..."
date: 2009-12-01
forum: General Help
---

### Post by airplaneman on 2009-12-01
Ok so I got tired of Ubuntu 9.1 NBR and I wanted to reinstall XP on my netbook (Asus EeePC 1005HA) but I couldn't find a way to uninstall Ubuntu (searched google and everything said put your windows install CD in). I don't have a CD drive so I made a bootable XP usb key but for some reason it won't load on the netbook..I tried a few other things and eventually got frustrated and just formatted the hard drive (put it into my external case and used my other comp). When I put the HDD back in and set it all up again, I get a GRUB error and it goes straight to the grub recovery console.

I still can't get it to boot from the USB key (which works on my other comp) and I don't know what to do. I have tried everything I can think of and would appreciate some help.

Thanks, and the faster the better since I want to get this thing back up and running hopefully by tomorrow.

---

### Post by Sin@Sin-Sacrifice on 2009-12-01
May not be able to boot from a thumb drive. Check in your BIOS under the boot configuration to see if a usb drive is an available option. If not then I don't know what to tell you.

---

### Post by switch10 on 2009-12-01
hey man,
there should be an option in BIOS that will allow you to boot from USB.  Also make sure in your boot order you have your USB booting before your hard drive.  In my my BIOS for some reason to enable USB devices the option is called "enable legacy usb devices".  

Good luck

Dave

---

### Post by SteveHillier on 2009-12-01
When you formatted your disk using your other computer did you just format it or did you delete the partitions on that disk.

If you have never done that in Windows try this.

Go to Right mouse on My Computer in the start menu (ie click Start first).  
Click Manage.
Then find Disk Management and click once.  All your disks should then appear.  Find the disk you want to change.  Right click over the hatched area.  You should find the Dlete Partition appear in the context menu.

Please, please, please ensure you do this on the disk you want to change.  Get it wrong and you might have two dead computers.

---

### Post by searchfgold6789 on 2009-12-01
the ONLY WAY to fix this problem is to get a cd drive, then use the XP disk's recovery console to delete ALL partitions on the disk, then fix the master boot record. How to:
1. Get the CD drive, and install it. This should be easy and there are plenty of guides on the internet.
2. Put the Windows XP disk into the CD drive.
3. Wait for it to load, if an error comes up, try try again and it will eventually work.
4. Press R (or f3 or whatever it says) to enter the recovery console.
5. Type "1" then press enter.
6. type FIXMBR. accept everything.
7. Type DISKPART and use the tool to delete any leftover partitions you see.
8. type EXIT or maybe QUIT to restart your computer. Boot back into the Wndows XP disk.
9. Install Windows.
Have fun.
NOTE: I don't think you can boot from USB devices.

---

### Post by searchfgold6789 on 2009-12-01
Yes i think there s an option to boot from USB in BIOS. Buy a cheap (5-10$) external CD drive from eBay and boot from it. Trust me, the CD is the way to go.

---

### Post by airplaneman on 2009-12-01
> **Sin@Sin-Sacrifice said:**
> May not be able to boot from a thumb drive. Check in your BIOS under the boot configuration to see if a usb drive is an available option. If not then I don't know what to tell you.

I do have the option..well it's called "removable device" so I assume that is a USB drive.

Thanks.

> **switch10 said:**
> hey man,
there should be an option in BIOS that will allow you to boot from USB.  Also make sure in your boot order you have your USB booting before your hard drive.  In my my BIOS for some reason to enable USB devices the option is called "enable legacy usb devices".  

Good luck

Dave

I have it set USB then CD then HDD, I'll check for that legacy usb devices option.

Thanks.

> **SteveHillier said:**
> When you formatted your disk using your other computer did you just format it or did you delete the partitions on that disk.

If you have never done that in Windows try this.

Go to Right mouse on My Computer in the start menu (ie click Start first).  
Click Manage.
Then find Disk Management and click once.  All your disks should then appear.  Find the disk you want to change.  Right click over the hatched area.  You should find the Dlete Partition appear in the context menu.

Please, please, please ensure you do this on the disk you want to change.  Get it wrong and you might have two dead computers.

I deleted the partitions..according to windows it is just ~155 GB of unallocated space (160GB HDD).

Thanks.

> **searchfgold6789 said:**
> the ONLY WAY to fix this problem is to get a cd drive, then use the XP disk's recovery console to delete ALL partitions on the disk, then fix the master boot record. How to:
1. Get the CD drive, and install it. This should be easy and there are plenty of guides on the internet.
2. Put the Windows XP disk into the CD drive.
3. Wait for it to load, if an error comes up, try try again and it will eventually work.
4. Press R (or f3 or whatever it says) to enter the recovery console.
5. Type "1" then press enter.
6. type FIXMBR. accept everything.
7. Type DISKPART and use the tool to delete any leftover partitions you see.
8. type EXIT or maybe QUIT to restart your computer. Boot back into the Wndows XP disk.
9. Install Windows.
Have fun.
NOTE: I don't think you can boot from USB devices.

I will see if I can get hold of an external CD drive and try this.

Thanks.

---

### Post by airplaneman on 2009-12-01
Well I somehow got it to load my USB key but I didn't see an option for recovery so I just installed..it seems to be working fine but occasionally (only when the bootable USB is in) I get a missing hal.dll error..not sure why.

---

### Post by switch10 on 2009-12-02
> **airplaneman said:**
> Well I somehow got it to load my USB key but I didn't see an option for recovery so I just installed..it seems to be working fine but occasionally (only when the bootable USB is in) I get a missing hal.dll error..not sure why.

That might not be anything to worry about apparently changing your boot order can bring up that error message up sometimes.  Did you get it installed with that USB key?  I'm interested to hear if it worked.  Did you use ubuntu's "make a bootable USB key" tool to make it?

---

### Post by airplaneman on 2009-12-02
> **switch10 said:**
> That might not be anything to worry about apparently changing your boot order can bring up that error message up sometimes.  Did you get it installed with that USB key?  I'm interested to hear if it worked.  Did you use ubuntu's "make a bootable USB key" tool to make it?

I got XP installed with the USB, yeah. I don't know what I did but I somehow got some boot options on startup and followed the onscreen options and just formatted the HDD and installed XP. I didn't use ubuntu's tool, I formatted the drive that had ubuntu on it which was the cause of this whole mess in the first place.

---

