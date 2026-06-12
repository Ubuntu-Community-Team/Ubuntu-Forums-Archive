---
title: "Ubuntu and acer laptop hidden recovery partition"
date: 2010-08-17
forum: General Help
---

### Post by occams_beard on 2010-08-17
I just got a new acer laptop that came loaded with Win 7, and I want to dual boot with Ubuntu.

Naturally the laptop didn't come with a Win 7 disc, but instead has the stupid recovery partition. I've made the recovery DVDs from the eRecovery program but....

From what I read the acer recovery setup is extremely picky and will refuse to work after the partitions have been messed with. Apparently the ALT+F10 to start the recovery process on boot won't even work if acer's MBR is overwritten. What's worse, even the recovery DVDs won't work without the MBR! (At least from what I've been reading... I guess if you install a different HD you are SOL)

So how does one get around this? I couldn't care less about acer's stupid recovery partition, but if I ever need to send the computer in for service I think they actually charge extra to restore their crap.

Any pointers or tips would really help! 

Thanks

---

### Post by ram2500 on 2010-08-17
I am assuming that the recovery discs are bootable, so I would try getting into BIOS to boot to the CD/DVD drive, if you haven't already done so. 

Another option (or options) would be to either call Acer and explain your situation, or contact Microsoft and speak with them regarding an issue with not having reinstallation media that works. I know, it's not their responsibility, but so long as you have a valid OEM key affixed to your computer and $30 or so, you will most likely get a replacement installation disc. Or, you can borrow a Windows 7 disc from someone not to install, but to repair the boot record (that is, if you haven't formatted the drive.) THe commands, which you'll type into Recovery Console, would be as follows: "bootrec /fixmbr" and "bootrec /fixboot".

---

### Post by occams_beard on 2010-08-17
> **ram2500 said:**
> I am assuming that the recovery discs are bootable, so I would try getting into BIOS to boot to the CD/DVD drive, if you haven't already done so. 

Another option (or options) would be to either call Acer and explain your situation, or contact Microsoft and speak with them regarding an issue with not having reinstallation media that works. I know, it's not their responsibility, but so long as you have a valid OEM key affixed to your computer and $30 or so, you will most likely get a replacement installation disc. Or, you can borrow a Windows 7 disc from someone not to install, but to repair the boot record (that is, if you haven't formatted the drive.) THe commands, which you'll type into Recovery Console, would be as follows: "bootrec /fixmbr" and "bootrec /fixboot".


Thanks, I understand about repairing the MBR for windows, however from what I read Acer apparently installs a hook into the MBR that ships with their systems to launch their recovery app. Even the DVDs are not supposed to work if the Acer MBR has been changed, which seems crazy to me.

---

### Post by cmcanulty on 2010-08-17
I put Ubuntu on my Acer netbook without a problem. I tried WUBI first and that was fine. But I didn't want to keep the windows on it at all. Only hassle was getting the wireless working which I did after a few questions on the forum.

---

### Post by pricetech on 2010-08-17
Before you do anything with Windows 7, go to Microsoft's website and download and install the Windows AIK for Windows 7.  Build a Windows PE disk with imagex on it and use that to create an image of your Windows 7 install.  Once that's done, you should be able to wipe the partitions and do pretty much as you please with the drive.

You might want to see if you can scrounge a second drive for the laptop for testing purposes just to be sure.

I'd call Acer and pitch a hissy fit from hell over the lack of media if was me.  It might not get you media, but it will make you feel better.

---

